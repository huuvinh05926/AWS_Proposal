---
title: "Đóng gói với Docker"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 5.5.1 </b> "
---

#### Đóng gói với Docker

Trước khi đưa lên Cloud, chúng ta cần đóng gói ứng dụng .NET Core thành một Docker Image.

#### 1. Tạo Dockerfile

Tại thư mục gốc của Solution, tạo file tên là **Dockerfile** (không có đuôi)

![docker1](/images/5-Workshop/5.5-Policy/docker1.png)

```dockerfile
# GIAI ĐOẠN 1: BUILD
FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests

# GIAI ĐOẠN 2: RUNTIME
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app

# Tạo user non-root để chạy ứng dụng (security best practice)
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring

# Copy JAR từ build stage
COPY --from=build /app/target/*.jar app.jar

# Expose port
EXPOSE 8085

# Health check (comment out nếu không có Spring Actuator)
# HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
#   CMD wget --no-verbose --tries=1 --spider http://localhost:8085/actuator/health || exit 1

# Run application
ENTRYPOINT ["java", "-jar", "app.jar"]
```

#### 2. Tạo buildspec.yml

Tạo file **buildspec.yml** để hướng dẫn AWS CodeBuild cách đóng gói và đẩy lên ECR

![docker2](/images/5-Workshop/5.5-Policy/docker2.png)

```yaml
version: 0.2

phases:
  pre_build:
    commands:
      - echo Logging in to Amazon ECR...
      # --- CẤU HÌNH THÔNG TIN ---
      - AWS_DEFAULT_REGION=ap-southeast-1
      # Thay Account ID của bạn vào dòng dưới:
      - AWS_ACCOUNT_ID= ACCOUNT ID CỦA BẠN
      - IMAGE_REPO_NAME=market-app
      - IMAGE_TAG=$(echo $CODEBUILD_RESOLVED_SOURCE_VERSION | cut -c 1-7)
      - REPOSITORY_URI=$AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$IMAGE_REPO_NAME
      # ---------------------------
      - aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com

  build:
    commands:
      - echo Build started on `date`
      - echo Building the Docker image...
      - docker build -t $REPOSITORY_URI:latest .
      - docker tag $REPOSITORY_URI:latest $REPOSITORY_URI:$IMAGE_TAG

  post_build:
    commands:
      - echo Build completed on `date`
      - echo Pushing the Docker image...
      - docker push $REPOSITORY_URI:latest
      - docker push $REPOSITORY_URI:$IMAGE_TAG
      - echo Writing image definitions file...
      # Tự động tạo file cấu hình Dockerrun.aws.json cho Beanstalk
      # Map Port 80 (Host) vào 8080 (Container .NET)
      - printf '{"AWSEBDockerrunVersion":"1","Image":{"Name":"%s","Update":"true"},"Ports":[{"ContainerPort":8080,"HostPort":80}]}' "$REPOSITORY_URI:$IMAGE_TAG" > Dockerrun.aws.json
      - cat Dockerrun.aws.json

artifacts:
  files:
    - Dockerrun.aws.json
```
