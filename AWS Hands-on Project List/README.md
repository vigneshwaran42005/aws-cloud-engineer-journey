# 🚀 AWS Cloud Engineer – Hands-on Projects

## 📌 About This Repository

This repository contains my hands-on AWS projects and practical learning journey as an aspiring AWS Cloud Engineer.

I have practiced AWS networking, compute, storage, databases, serverless architecture, messaging, automation, load balancing, high availability and security concepts.

---

# 🏗️ Project 01 – VPC & EC2 Infrastructure

### AWS Services
VPC, Subnets, Availability Zones, Internet Gateway, Route Tables, EC2, Security Groups

### Architecture

    Internet
        |
        v
    Internet Gateway
        |
        v
    AWS VPC
        |
        +--------------------+
        |                    |
        v                    v
    Public Subnet        Private Subnet
        |                    |
        v                    v
    Public EC2           Private EC2

### What I Practiced

- Created a custom VPC
- Configured public and private subnets
- Worked with Availability Zones
- Created Internet Gateway
- Configured Route Tables
- Launched EC2 instances
- Configured Security Groups
- Tested EC2 network connectivity

### Key Learning

Learned how VPC, subnets, route tables, Internet Gateway and EC2 work together to build AWS network infrastructure.

---

# 🔐 Project 02 – Bastion Host Architecture

### AWS Services
VPC, Public Subnet, Private Subnet, EC2, Security Groups, RDP/SSH

### Architecture

    Internet
        |
        v
    Public EC2
    Bastion Host
        |
        | RDP / SSH
        v
    Private EC2

### What I Practiced

- Created a public EC2 instance as Bastion Host
- Created a private EC2 instance
- Configured Security Groups
- Connected to the Bastion Host
- Accessed the private EC2 through the Bastion Host
- Practiced secure administrative access to private infrastructure

### Key Learning

Learned how a Bastion Host can provide controlled administrative access to EC2 instances inside a private subnet.

---

# 🔗 Project 03 – VPC Peering with IIS Web Servers

### AWS Services
VPC, VPC Peering, Windows EC2, IIS, Route Tables, Security Groups

### Architecture

    VPC 1
       |
       v
    Windows EC2
       |
       | VPC Peering
       |
       v
    VPC 2
       |
       v
    Windows EC2 + IIS

### What I Practiced

- Created two VPCs with non-overlapping CIDR blocks
- Created Windows EC2 instances in both VPCs
- Installed IIS on both servers
- Created HTML pages on both IIS servers
- Created VPC Peering Connection
- Updated Route Tables
- Configured Security Groups
- Tested private communication between VPCs
- Accessed the VPC 2 IIS webpage from VPC 1 using private IP and HTTP port 80

### Key Learning

Learned how VPC Peering enables private communication between two VPCs.

---

# ⚖️ Project 04 – Application Load Balancer with Multiple EC2 Servers

### AWS Services
VPC, Availability Zones, Public/Private Subnets, EC2, IIS, ALB, Target Groups, Security Groups

### Architecture

    Internet
        |
        v
    Application Load Balancer
        |
        v
    Target Group
        |
        +-------- EC2-1
        |
        +-------- EC2-2

### What I Practiced

- Created four subnets across Availability Zones
- Created two public EC2 instances
- Created two private EC2 instances
- Installed IIS
- Created different HTML pages
- Created Target Groups
- Configured Health Checks
- Created Application Load Balancer
- Configured Load Balancer Security Group
- Used the Load Balancer Security Group as the source in EC2 Security Groups
- Allowed traffic from ALB to EC2
- Accessed the ALB DNS name from Chrome
- Tested traffic distribution between EC2 instances

### Key Learning

Learned how an Application Load Balancer distributes incoming traffic across healthy EC2 instances.

---

# 📈 Project 05 – Auto Scaling with Launch Template

### AWS Services
EC2, Launch Template, Auto Scaling Group, CloudWatch, Windows, PowerShell

### Architecture

    Launch Template
          |
          v
    Auto Scaling Group
          |
          v
       EC2-1
          |
          v
    High CPU Utilization
          |
          v
    Scaling Policy
          |
          v
       EC2-2

### What I Practiced

- Created Launch Template
- Created Auto Scaling Group
- Configured Minimum Capacity = 1
- Configured Maximum Capacity = 3
- Configured Desired Capacity
- Configured CPU-based scaling
- Connected to Windows EC2 using RDP
- Generated CPU load using PowerShell
- Observed CPU utilization
- Waited for scaling condition
- Observed automatic EC2 instance creation
- Practiced Scale-Out
- Practiced Scale-In
- Learned Auto Scaling termination behavior

### Key Learning

Learned how Auto Scaling automatically adjusts EC2 capacity based on defined scaling policies.

---

# 🌐 Project 06 – S3 Static Website Hosting

### AWS Services
S3, Static Website Hosting, HTML, Bucket Policy

### Architecture

    User / Chrome
         |
         v
    S3 Bucket
         |
         v
    index.html
         |
         v
    Static Website Endpoint
         |
         v
    Web Page

### What I Practiced

- Created S3 Bucket
- Uploaded index.html
- Enabled Static Website Hosting
- Configured required public access settings
- Configured Bucket Policy
- Generated S3 Website Endpoint
- Opened the website from Chrome

### Key Learning

Learned how Amazon S3 can be used to host static website content.

---

# 🔄 Project 07 – S3 Replication

### AWS Services
S3, Versioning, IAM

### Architecture

    Source S3 Bucket
           |
           v
    Replication Rule
           |
           v
    Destination S3 Bucket

### What I Practiced

- Created Source S3 Bucket
- Created Destination S3 Bucket
- Enabled required Versioning
- Created Replication Rule
- Configured IAM Replication Role
- Uploaded objects to Source Bucket
- Verified replicated objects in Destination Bucket

### Key Learning

Learned how S3 Replication automatically copies objects from a source bucket to a configured destination bucket.

---

# 🌍 Project 08 – S3 CORS Cross-Origin Access

### AWS Services
S3, HTML, CORS, Bucket Policy

### Architecture

    Source S3 Website
          |
          v
      HTML Button
          |
          v
    Cross-Origin Request
          |
          v
    Destination S3
          |
          v
    Destination HTML

### What I Practiced

- Created Source S3 Bucket
- Created Destination S3 Bucket
- Created HTML pages in both buckets
- Added button to Source HTML
- Requested a resource from Destination S3
- Observed CORS error
- Configured CORS on Destination Bucket
- Configured required access policy
- Tested the request again
- Successfully accessed the Destination HTML page

### Key Learning

Learned how CORS controls browser-based cross-origin access between different origins.

---

# ⚡ Project 09 – S3 → Lambda → DynamoDB Resume Processing

### AWS Services
S3, Lambda, DynamoDB, IAM, Python, Lambda Layer

### Architecture

    User
      |
      | Upload Resume
      v
    S3 Bucket
      |
      | S3 Trigger
      v
    Lambda Function
      |
      | Process Resume
      v
    DynamoDB

### What I Practiced

- Created S3 Bucket
- Created Lambda Function
- Used Python runtime
- Configured S3 Trigger
- Created DynamoDB Table
- Configured Lambda IAM permissions
- Added required Python dependencies using Lambda Layer
- Uploaded resume
- Triggered Lambda automatically
- Processed resume information
- Stored required data/reference in DynamoDB

### Key Learning

Learned how S3 events can trigger Lambda to process uploaded files and store required information in DynamoDB.

---

# ⏰ Project 10 – EventBridge Scheduled Report Generation

### AWS Services
EventBridge, Lambda, S3, DynamoDB

### Architecture

    DynamoDB
        |
        v
    EventBridge
    Every 2 Minutes
        |
        v
    Lambda
        |
        v
    Generate Report
        |
        v
    S3 Bucket

### What I Practiced

- Extended the previous S3 + Lambda + DynamoDB project
- Created EventBridge Schedule
- Configured 2-minute interval for testing
- Configured EventBridge to invoke Lambda
- Lambda processed required data
- Generated a report
- Stored report in S3
- Verified scheduled execution

### Key Learning

Learned how EventBridge Scheduler can automatically trigger Lambda based on a defined schedule.

---

# 📢 Project 11 – S3 → SNS → SQS Notification

### AWS Services
S3, SNS, SQS

### Architecture

    User
      |
      | Upload Resume
      v
    S3 Bucket
      |
      v
    SNS Topic
      |
      v
    SQS Queue
      |
      v
    Message

### What I Practiced

- Created S3 Bucket
- Configured resume upload event
- Created SNS Topic
- Configured notification
- Created SQS Queue
- Connected SQS as SNS subscriber
- Uploaded a resume
- Verified SNS notification
- Verified message inside SQS Queue

### Key Learning

SNS:
- Publish
- Notify
- Fan-out

SQS:
- Queue
- Store messages for processing
- Asynchronous processing

---

# 📧 Project 12 – Automated Resume Processing & Email Notification

### AWS Services
S3, Lambda ×2, DynamoDB, SNS, SES, Lambda Layer, IAM, Python

### Architecture

    Candidate
        |
        | Upload Resume
        v
    S3 Bucket
        |
        +-----------------------+
        |                       |
        v                       v
    Lambda 1                Lambda 2
        |                       |
        |                       +------> SNS
        |                       |          |
        |                       |          v
        |                       |       My Email
        |                       |
        |                       +------> Extract Candidate Email
        |                                  |
        |                                  v
        |                                 SES
        |                                  |
        |                                  v
        |                          Candidate Email
        |                          "Thank You for Upload"
        |
        v
    DynamoDB

### Lambda 1 – Resume Processing

- Triggered by S3
- Read the uploaded resume
- Extracted resume data
- Used Python PDF/data extraction dependencies
- Created and attached Lambda Layer
- Configured required IAM permissions
- Stored extracted information in DynamoDB

### Lambda 2 – Notification & Email

- Triggered by S3 upload
- Published upload notification through SNS
- Sent notification to my email
- Extracted candidate email from the resume
- Used Amazon SES to send a thank-you email to the candidate
- Configured Environment Variables
- Configured required IAM permissions
- Verified Gmail identity in SES
- Deployed and tested the complete workflow

### Key Learning

    S3
     |
     +------------------+
     |                  |
     v                  v
    Lambda 1         Lambda 2
     |                  |
     v                  +----> SNS ----> My Email
    DynamoDB            |
                        +----> SES ----> Candidate Email

This project helped me understand serverless, event-driven resume processing and email automation.

---

# 📂 Project 13 – EFS Shared File System

### AWS Services
EFS, EC2, Linux, VPC, Security Groups

### Architecture

    Linux EC2-1
         |
         | Mount
         v
    Amazon EFS
         ^
         | Mount
         |
    Linux EC2-2

### What I Practiced

- Created Amazon EFS
- Created two Linux EC2 instances
- Configured required networking
- Configured Security Groups
- Mounted EFS on Linux EC2-1
- Mounted the same EFS on Linux EC2-2
- Created a test file from EC2-1
- Checked the same EFS directory from EC2-2
- Verified that the same file was visible from both servers

### Testing

    EC2-1
       |
       | Create test.txt
       v
    Amazon EFS
       |
       | Shared Storage
       v
    EC2-2
       |
       v
    test.txt visible

### Key Learning

Learned how Amazon EFS provides shared file storage that can be mounted and accessed by multiple EC2 instances.

---

# 🏆 AWS Services Practiced

## Networking
- VPC
- Subnets
- Availability Zones
- Route Tables
- Internet Gateway
- VPC Peering

## Compute
- EC2
- Launch Templates
- Auto Scaling Groups

## Load Balancing
- Application Load Balancer
- Target Groups
- Health Checks

## Storage
- Amazon S3
- S3 Replication
- S3 Static Website Hosting
- Amazon EFS

## Serverless
- AWS Lambda
- Amazon EventBridge
- DynamoDB

## Messaging
- Amazon SNS
- Amazon SQS

## Email
- Amazon SES

## Security
- IAM
- IAM Roles
- IAM Permissions
- Security Groups
- S3 Bucket Policies
- CORS

## Other Technologies
- Windows Server
- Linux
- IIS
- Python
- HTML
- Lambda Layers
- PowerShell
- RDP / SSH

---

# 🎯 Overall Learning Outcome

Through these hands-on projects, I gained practical experience in designing and implementing AWS infrastructure using networking, compute, storage, databases, serverless services, messaging, automation, security and high-availability concepts.

My AWS hands-on journey includes:

    Networking
        ↓
    Compute
        ↓
    Storage
        ↓
    Databases
        ↓
    Serverless
        ↓
    Messaging
        ↓
    Automation
        ↓
    High Availability
        ↓
    Cloud Architecture

---

## 🚀 AWS Cloud Engineer – Hands-on Learning Journey

**13 Hands-on Projects | Multiple AWS Services | Practical Cloud Architecture**
