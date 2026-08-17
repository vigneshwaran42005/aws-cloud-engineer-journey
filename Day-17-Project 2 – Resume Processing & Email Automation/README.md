# Project 2 – Resume Processing & Email Automation 📄📧

## 📌 Project Overview

In this project, I created **two AWS Lambda functions** to automate resume processing and email notifications.

When a user uploads a resume PDF to an S3 bucket:

* **Lambda 1** extracts the resume data and stores it in DynamoDB.
* **Lambda 2** handles notification and email automation.
* **SNS** is used to notify me that a resume has been uploaded.
* **Amazon SES** is used to send a thank-you email to the candidate using the email address extracted from the resume.

## 🏗️ Project Architecture

```text
                              User
                               │
                               │ Upload Resume PDF
                               ↓
                          Amazon S3
                               │
                  ┌────────────┴────────────┐
                  │                         │
             S3 Trigger                S3 Event
                  │                         │
                  ↓                         ↓
             Lambda 1                   Lambda 2
                  │                         │
                  │                         ├──── SNS
                  │                         │      │
                  │                         │      ↓
                  │                         │   My Email
                  │                         │
                  │                         └──── Extract
                  │                              Candidate Email
                  │                                   │
                  ↓                                   ↓
              DynamoDB                              SES
                                                       │
                                                       ↓
                                              Candidate Email
                                             "Thank You for Upload"
```

## ⚡ Lambda Function 1 – Resume Data Processing

The first Lambda function is responsible for processing the uploaded resume.

### Workflow

```text
S3 Resume Upload
       ↓
S3 Trigger
       ↓
Lambda Function 1
       ↓
Read Resume
       ↓
Extract Resume Data
       ↓
Store Data
       ↓
DynamoDB
```

The Lambda function extracts the required information from the uploaded resume and stores the data in a DynamoDB table.

### Example Data

The extracted information can include:

* Candidate Name
* Email Address
* Phone Number
* Skills
* Other required resume details

## 📦 Lambda Layer

Since the Lambda function required additional Python libraries for PDF/resume data extraction, I created and attached a **Lambda Layer** containing the required dependencies.

```text
Lambda 1
   │
   ├── Python Code
   │
   └── Lambda Layer
          │
          └── PDF/Data Extraction Libraries
```

This allowed the Lambda function to use the required external Python packages.

## 🔐 Lambda 1 Permissions

I configured the required IAM permissions for Lambda 1.

The Lambda execution role was given the permissions required to:

```text
Lambda 1
   │
   ├── Read Resume from S3
   │
   └── Write Extracted Data → DynamoDB
```

The permissions were configured according to the required AWS resources and actions.

## 🗄️ DynamoDB

The extracted resume information was stored in a DynamoDB table.

```text
Resume PDF
    ↓
Lambda 1
    ↓
Extract Data
    ↓
DynamoDB Table
```

This allowed the candidate information to be stored in a structured NoSQL database.

---

# 📩 Lambda Function 2 – Notification & Email Automation

The second Lambda function is responsible for the **notification and email workflow**.

When a resume is uploaded to S3, Lambda 2 processes the event and performs two important tasks:

1. Sends an upload notification using **SNS**
2. Extracts the candidate's email and sends a thank-you email using **Amazon SES**

## 🔔 SNS Notification

When a resume is uploaded, Lambda 2 publishes a notification to an SNS Topic.

```text
Resume Upload
     ↓
Lambda 2
     ↓
SNS Topic
     ↓
My Email
```

The notification informs me that a new resume has been uploaded.

Example:

> New resume uploaded successfully.

## 📧 Candidate Email Extraction

The uploaded resume contains the candidate's email address.

Lambda 2 extracts the candidate's email address from the resume data.

```text
Resume
   ↓
Lambda 2
   ↓
Extract Candidate Email
   ↓
Amazon SES
```

## ✉️ Amazon SES

I used **Amazon SES (Simple Email Service)** to send an automated thank-you email to the candidate.

Example workflow:

```text
Candidate Uploads Resume
          ↓
       S3 Bucket
          ↓
       Lambda 2
          ↓
Extract Candidate Email
          ↓
       Amazon SES
          ↓
Candidate Email
```

The email can contain a message such as:

> Thank you for uploading your resume. We have successfully received your application.

## 🔐 Lambda 2 Permissions

I configured the required IAM permissions for Lambda 2.

```text
Lambda 2
   │
   ├── S3 Access
   ├── SNS Publish Permission
   └── SES Send Email Permission
```

These permissions allow Lambda 2 to perform the required notification and email operations.

## ⚙️ Environment Variables

I also configured the required **Lambda Environment Variables** for values such as:

* SNS Topic ARN
* DynamoDB table information
* SES configuration
* Other application-specific values

Using environment variables avoids hard-coding configuration values directly into the Python code.

## 📧 SES Verification

For testing, I verified the required email identity in Amazon SES.

Because the SES account was in the **sandbox environment**, email sending was restricted according to SES sandbox requirements.

Therefore, the verified email addresses were used for testing.

---

# 📬 Optional SQS Integration

I also learned that **Amazon SQS** can be added to this workflow when asynchronous processing and message queuing are required.

For example:

```text
S3
 ↓
Lambda 2
 ↓
SNS
 ↓
SQS Queue
 ↓
Consumer / Lambda
 ↓
Process Message
```

### SNS vs SQS

**SNS:**

> Used to publish and distribute notifications.

**SQS:**

> Used to place messages in a queue so that they can be processed asynchronously.

```text
SNS → Notify / Fan-out

SQS → Queue / Wait / Process
```

If SQS is included in the actual implementation, it can act as a buffer between the producer and consumer.

---

# 🧪 Complete Hands-on Practice

During this project, I practiced:

1. Created an S3 bucket
2. Created two Lambda functions
3. Configured S3 triggers
4. Created a Lambda Layer
5. Added required Python PDF/data extraction dependencies
6. Attached the Layer to Lambda
7. Configured Lambda 1 permissions
8. Configured Lambda 2 permissions
9. Created a DynamoDB table
10. Configured Lambda 1 to process the resume
11. Extracted resume data
12. Stored the extracted data in DynamoDB
13. Created an SNS Topic
14. Configured Lambda 2 to publish an SNS notification
15. Configured SNS email notification to my email
16. Extracted the candidate email from the resume
17. Configured Amazon SES
18. Verified the required Gmail identity
19. Configured SES permissions for Lambda
20. Configured required Lambda environment variables
21. Added the required Python code
22. Deployed the Lambda functions
23. Uploaded a resume to S3
24. Verified Lambda execution
25. Verified DynamoDB data
26. Verified SNS notification
27. Verified the automated candidate email
28. Checked execution logs and confirmed successful execution

# 🔄 Final Project Flow

```text
                         USER
                           │
                           │ Upload Resume
                           ↓
                      S3 BUCKET
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ↓                           ↓
        LAMBDA 1                    LAMBDA 2
             │                           │
             │                           ├──── SNS
             │                           │      │
             │                           │      ↓
             │                           │   MY EMAIL
             │                           │
             │                           └──── Extract
             │                                Candidate Email
             │                                      │
             ↓                                      ↓
        DYNAMODB                                  SES
                                                     │
                                                     ↓
                                           CANDIDATE EMAIL
                                         "Thank You for Upload"
```

# 💡 Key Learning

This project helped me understand how multiple AWS services can be combined to build a **serverless, event-driven automation system**.

The main responsibilities were:

```text
Lambda 1
→ Extract Resume Data
→ Store Data in DynamoDB

Lambda 2
→ Upload Notification using SNS
→ Extract Candidate Email
→ Send Thank-you Email using SES
```

## 🎯 Project Outcome

Successfully designed and practiced an automated **resume processing and notification system** where a resume uploaded to S3 triggers Lambda-based processing.

The system processes the resume data, stores candidate information in DynamoDB, sends an upload notification through SNS, and sends an automated thank-you email to the candidate through Amazon SES.

## 🚀 AWS Services Practiced

* Amazon S3
* AWS Lambda
* Amazon DynamoDB
* Amazon SNS
* Amazon SQS
* Amazon SES
* Lambda Layers
* IAM Roles & Permissions
* Python
* Environment Variables
* Event-Driven Architecture
* Serverless Architecture
* Resume Data Extraction
* Automated Email Notification
