---
title: "Các bài blogs đã dịch"
date: "2025-11-11"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Tại đây sẽ là phần liệt kê, giới thiệu các blogs mà các bạn đã dịch. Ví dụ:

### [Blog 1 - Tự động hóa Quản lý Ngân sách trong Môi trường Đa Tài Khoản](3.1-Blog1/)

Blog này trình bày cách tự động hóa quản lý ngân sách trên nhiều tài khoản AWS bằng kiến trúc hướng sự kiện (event-driven). Giải pháp cho phép quản lý ngân sách tập trung với thông báo email tự động, giúp tổ chức có thể thiết lập và áp dụng ngân sách riêng cho từng tài khoản từ một tài khoản quản lý trung tâm. Các công nghệ chính bao gồm Amazon DynamoDB để lưu trữ giá trị ngân sách, AWS Lambda để phân phối cấu hình ngân sách thông qua AWS Systems Manager Parameter Store, và AWS Budgets để giám sát chi tiêu theo thời gian thực. Bài viết cung cấp các bước triển khai chi tiết sử dụng CloudFormation templates và giải thích cách xử lý trạng thái cảnh báo ngân sách cũng như triển khai các cải tiến trong tương lai như AWS Budget Actions và tích hợp ServiceNow để tối ưu hóa chi phí tự động.

### [Blog 2 - Hướng dẫn xây dựng Media Lake trên AWS](3.2-Blog2/)

Blog này giới thiệu một giải pháp toàn diện để xây dựng media lake tập trung trên AWS nhằm quản lý khối lượng lớn các tệp phương tiện số rải rác trên nhiều Amazon S3 buckets. Hướng dẫn cung cấp kiến trúc tham chiếu tạo ra giao diện tìm kiếm thống nhất, cho phép người dùng tìm kiếm các tệp phương tiện trên tất cả các vị trí S3 đồng thời. Giải pháp bao gồm các pipeline xử lý phương tiện tự động theo sự kiện sử dụng giao diện kéo thả, khả năng tìm kiếm ngôn ngữ tự nhiên được hỗ trợ bởi AI, và tích hợp liền mạch với các dịch vụ AWS. Giải pháp có thể được triển khai qua ba phương thức: AWS CloudFormation template, triển khai cục bộ sử dụng AWS CDK, hoặc tích hợp với pipeline CI/CD hiện có, mang lại sự linh hoạt cho các nhu cầu tổ chức khác nhau.

### [Blog 3 - Cập nhật cấu hình động trong .NET sử dụng Parameter Store và Secrets Manager](3.3-Blog3/)

Blog này khám phá cách tiếp cận nâng cao để quản lý cấu hình và secrets trong ứng dụng .NET sử dụng AWS Systems Manager Parameter Store và AWS Secrets Manager. Giải pháp minh họa cách tham chiếu secrets của Secrets Manager thông qua Parameter Store bằng định dạng `/aws/reference/secretsmanager/`, cho phép truy cập thống nhất vào cả cấu hình và dữ liệu nhạy cảm. Các tính năng chính bao gồm triển khai tải lại cấu hình động mà không cần khởi động lại ứng dụng sử dụng IOptionsMonitor pattern, phân tách môi trường thông qua cấu trúc phân cấp của Parameter Store, và lưu trữ an toàn với mã hóa và kiểm soát truy cập phù hợp. Bài viết cung cấp các ví dụ mã C# từng bước hướng dẫn cách thiết lập extension methods, configuration models, và dependency injection để tích hợp liền mạch với ứng dụng .NET 8.
