# Day 14 – AWS Lambda & DynamoDB Serverless Project ⚡🗄️

## 📅 Topic

**AWS Lambda & Amazon DynamoDB**

## 📌 What I Learned

In this session, I learned about **AWS Lambda** and **Amazon DynamoDB** and how they can be used together to build a serverless application.

I also learned how an **S3 event can trigger a Lambda function**, which can then process the uploaded file and store the required information in DynamoDB.

## ⚡ AWS Lambda

AWS Lambda is a **serverless compute service** that allows us to run code without managing servers.

With Lambda, AWS manages the underlying infrastructure, while we focus on writing and running the application code.

### Key Benefits

* Serverless execution
* No server management
* Automatic scaling
* Pay only for execution
* Event-driven architecture

## 🗄️ Amazon DynamoDB

Amazon DynamoDB is a fully managed **NoSQL database service** designed for high performance and scalability.

Unlike a traditional relational database, DynamoDB does not require a fixed relational schema with predefined rows and columns.

DynamoDB stores data using:

```text
Table
  ↓
Items
  ↓
Attributes
```

Example:

```text
ResumeTable
   │
   ├── Item 1
   │    ├── ResumeID
   │    ├── FileName
   │    └── S3Path
   │
   └── Item 2
        ├── ResumeID
        ├── FileName
        └── S3Path
```

## 🏗️ Project Overview

For this hands-on project, I built a serverless workflow using:

* Amazon S3
* AWS Lambda
* Amazon DynamoDB
* IAM
* Lambda Layers
* Python

The objective was to upload a **resume PDF file to an S3 bucket**, trigger a Lambda function automatically, process the uploaded file information and store the required data in DynamoDB.

## 🏗️ Project Architecture

```text
                  User
                   │
                   │ Upload Resume
                   ↓
             Amazon S3 Bucket
                   │
                   │ S3 Event Trigger
                   ↓
             AWS Lambda Function
                   │
          ┌────────┴─────────┐
          │                  │
          ↓                  ↓
     S3 Object Data      Python Layer
          │                  │
          └────────┬─────────┘
                   ↓
             Process Data
                   │
                   ↓
             DynamoDB Table
```

## 🪣 Step 1 – S3 Bucket

I created an S3 bucket to store uploaded resume files.

Example:

```text
S3 Bucket
   │
   ├── resume1.pdf
   ├── resume2.pdf
   └── resume3.pdf
```

The S3 bucket acts as the initial storage location for the uploaded resumes.

## ⚡ Step 2 – Lambda Function

I created a Lambda function using **Python**.

The Lambda function was configured to execute whenever a new resume was uploaded to the S3 bucket.

```text
S3 Upload
    ↓
S3 Event
    ↓
Lambda Function
```

This demonstrates an **event-driven serverless architecture**.

## 🔔 Step 3 – S3 Trigger

I configured an **S3 trigger** for the Lambda function.

Whenever a new resume was uploaded to the configured S3 bucket, S3 generated an event that invoked the Lambda function.

```text
Resume Upload
      ↓
S3 Event Trigger
      ↓
Lambda Function
```

## 🐍 Step 4 – Python Lambda Code

I used Python code inside the Lambda function to process the S3 event and work with the uploaded resume.

The function obtained information such as the uploaded object's:

* Bucket name
* Object key
* File name
* S3 path

The processed information was then prepared for storage in DynamoDB.

## 🗄️ Step 5 – DynamoDB

I created a DynamoDB table to store the required resume information.

Example:

```text
DynamoDB Table
       │
       ├── Resume ID
       ├── File Name
       ├── S3 Bucket
       └── S3 Object Path
```

The actual PDF file remained stored in **S3**, while the required information/reference about the resume could be stored in DynamoDB.

## 🔐 Step 6 – IAM Permissions

The Lambda function required permission to interact with both S3 and DynamoDB.

I configured the required IAM permissions for the Lambda execution role.

Conceptually:

```text
Lambda Execution Role
        │
        ├── S3 Permissions
        │
        └── DynamoDB Permissions
```

This allowed Lambda to:

* Read the required S3 object/event information
* Write the processed information to DynamoDB

## 📦 Step 7 – Lambda Layer

Since the Python function required additional functionality for working with PDF-related processing, I created and attached a **Lambda Layer** containing the required Python dependencies.

```text
Lambda Function
      │
      ├── Python Code
      │
      └── Lambda Layer
             │
             └── Required Python Dependencies
```

This helped separate external dependencies from the main Lambda function code.

## 🔄 Complete Project Flow

```text
User
  │
  │ Upload Resume PDF
  ↓
S3 Bucket
  │
  │ S3 Event Trigger
  ↓
Lambda Function
  │
  ├── Read S3 Event
  ├── Get Resume Information
  ├── Process Required Data
  │
  ↓
DynamoDB
  │
  ↓
Resume Information Stored
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created an S3 bucket
2. Uploaded resume PDF files
3. Created a Lambda function
4. Selected Python as the Lambda runtime
5. Configured an S3 trigger
6. Created a DynamoDB table
7. Configured IAM permissions for Lambda
8. Added S3 permissions
9. Added DynamoDB permissions
10. Created Python-based Lambda code
11. Created a Lambda Layer
12. Added the required Python dependencies
13. Attached the Layer to the Lambda function
14. Uploaded a resume to the S3 bucket
15. Triggered the Lambda function automatically
16. Processed the S3 event
17. Stored the required resume information in DynamoDB
18. Verified the stored data in DynamoDB

## 💡 Key Learning

This project helped me understand how multiple AWS services can work together to build a **serverless, event-driven architecture**.

The most important flow I learned was:

```text
S3
 ↓
Event Trigger
 ↓
Lambda
 ↓
Python Processing
 ↓
DynamoDB
```

I also learned how **IAM permissions** control access between AWS services and how **Lambda Layers** can provide additional Python dependencies to a Lambda function.

## 🎯 Project Outcome

Successfully built a serverless workflow where uploading a resume to an **S3 bucket automatically triggered a Lambda function**, which processed the uploaded file information and stored the required data/reference in **DynamoDB**.

This hands-on project gave me practical experience with:

* Amazon S3
* AWS Lambda
* Amazon DynamoDB
* IAM Roles & Permissions
* S3 Event Triggers
* Python
* Lambda Layers
* Serverless Architecture
* Event-Driven Architecture
