---
title: "Configure Internet & NAT Gateway"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 5.3.2 </b> "
---

#### Create Internet Gateway

1. In the **VPC dashboard**, click on **Internet gateways**

![IGW1](/images/5-Workshop/5.3-S3-vpc/IGW1.png)

2. Then click on **Create internet gateway**

![IGW2](/images/5-Workshop/5.3-S3-vpc/IGW2.png)

3. In the Create internet gateway section, choose a name as you like, then click **Create internet gateway** and wait for it to be created

![IGW3](/images/5-Workshop/5.3-S3-vpc/IGW3.png)

4. After the Internet gateway is created, go to the **Actions** section and click **Attach to VPC** to attach it to the VPC created in the previous section

![IGW4](/images/5-Workshop/5.3-S3-vpc/IGW4.png)

![IGW5](/images/5-Workshop/5.3-S3-vpc/IGW5.png)

#### Create NAT Gateway

1. Create a NAT Gateway located in **Public Subnet 1**

2. Assign an **Elastic IP** to have a static address to the Internet

![NAT1](/images/5-Workshop/5.3-S3-vpc/NAT1.png)

![NAT2](/images/5-Workshop/5.3-S3-vpc/NAT2.png)

![Success](/images/5-Workshop/5.3-S3-vpc/start-session-success.png)

You have successfully start a session - connect to the EC2 instance in VPC cloud. In the next step, we will create a S3 bucket and a file in it.

#### Create a file and upload to s3 bucket

1. Change to the ssm-user's home directory by typing `cd ~` in the CLI

![Change user's dir](/images/5-Workshop/5.3-S3-vpc/cli1.png)

2. Create a new file to use for testing with the command `fallocate -l 1G testfile.xyz`, which will create a file of 1GB size named "testfile.xyz".

![Create file](/images/5-Workshop/5.3-S3-vpc/cli-file.png)

3. Upload file to S3 bucket with command `aws s3 cp testfile.xyz s3://your-bucket-name`. Replace your-bucket-name with the name of S3 bucket that you created earlier.

![Uploaded](/images/5-Workshop/5.3-S3-vpc/uploaded.png)

You have successfully uploaded the file to your S3 bucket. You can now terminate the session.

#### Check object in S3 bucket

1. Navigate to S3 console.
2. Click the name of your s3 bucket
3. In the Bucket console, you will see the file you have uploaded to your S3 bucket

![Check S3](/images/5-Workshop/5.3-S3-vpc/check-s3-bucket.png)

#### Section summary

Congratulation on completing access to S3 from VPC. In this section, you created a Gateway endpoint for Amazon S3, and used the AWS CLI to upload an object. The upload worked because the Gateway endpoint allowed communication to S3, without needing an Internet Gateway attached to "VPC Cloud". This demonstrates the functionality of the Gateway endpoint as a secure path to S3 without traversing the Public Internet.
