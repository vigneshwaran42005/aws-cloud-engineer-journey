# Day 15 – Amazon EventBridge Scheduler ⏰⚡

## 📅 Topic

**Amazon EventBridge – Scheduled Events & Serverless Automation**

## 📌 What I Learned

In this session, I learned about **Amazon EventBridge** and how scheduled events can be used to automatically trigger AWS services at a specific time or recurring interval.

For practice, I used a **2-minute schedule** to automatically generate a report from the data processed by the previous S3, Lambda and DynamoDB project.

## ⏰ What is Amazon EventBridge?

Amazon EventBridge is a serverless event service that can be used to connect AWS services and applications using events.

It can also be used to run tasks on a **scheduled basis**.

Example:

```text
Every 2 minutes
       ↓
EventBridge Schedule
       ↓
Lambda Function
       ↓
Generate Report
       ↓
S3 Bucket
```

## 🏗️ Project Overview

I extended my previous **S3 + Lambda + DynamoDB** project by adding Amazon EventBridge.

### Previous Project

```text
Resume Upload
      ↓
S3 Bucket
      ↓
S3 Event Trigger
      ↓
Lambda
      ↓
DynamoDB
```

### Updated Project

```text
Resume Upload
      ↓
S3 Bucket
      ↓
Lambda
      ↓
DynamoDB
      ↑
      │
EventBridge Scheduler
      │
Every 2 Minutes
      ↓
Lambda
      ↓
Generate Report
      ↓
S3 Bucket
```

## 🧑‍💼 Real-World Use Case

I understood the concept using an **HR reporting scenario**.

For example, an HR team may want to know how many resumes or candidates have been received during a particular period.

Instead of manually checking the database every time, a scheduled EventBridge workflow can automatically generate a report.

Example:

```text
Candidates / Resumes
        ↓
     DynamoDB
        ↓
EventBridge Schedule
        ↓
Every 2 Minutes
        ↓
Lambda
        ↓
Generate Report
        ↓
S3 Bucket
```

In a real production environment, the schedule could be changed from 2 minutes to a suitable interval such as hourly, daily or another required schedule.

## ⏱️ EventBridge Schedule

For my hands-on practice, I configured a schedule to run every **2 minutes**.

```text
EventBridge
     │
     │ Every 2 Minutes
     ↓
Lambda Function
```

The 2-minute interval was used only for testing and demonstration.

## ⚡ Lambda Integration

EventBridge was configured to invoke the Lambda function according to the schedule.

The Lambda function then performed the required report-generation process.

```text
EventBridge
     ↓
Lambda Function
     ↓
Process Data
     ↓
Generate Report
```

## 🪣 S3 Integration

The generated report was stored in an S3 bucket.

```text
Lambda
   ↓
Generate Report
   ↓
S3 Bucket
   ↓
Report File
```

This allowed the generated report to be stored and accessed later.

## 🔐 IAM Permissions

I configured the required IAM permissions so that the AWS services could communicate securely.

The Lambda execution role required permissions for the AWS resources used by the workflow.

Conceptually:

```text
EventBridge
     ↓
Invoke Lambda
     ↓
Lambda
 ┌───┴───────────┐
 ↓               ↓
DynamoDB         S3
Read Data       Store Report
```

The permissions follow the **Principle of Least Privilege**, allowing only the required actions.

## 🔄 Complete Project Flow

```text
                Resume Upload
                      │
                      ↓
                 S3 Bucket
                      │
                      ↓
               Lambda Function
                      │
                      ↓
                 DynamoDB
                      │
                      │
              EventBridge Scheduler
                      │
                 Every 2 Minutes
                      │
                      ↓
               Lambda Function
                      │
                      ↓
                Generate Report
                      │
                      ↓
                  S3 Bucket
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Reused the previous S3 + Lambda + DynamoDB project
2. Created an EventBridge schedule
3. Configured a 2-minute schedule for testing
4. Configured EventBridge to invoke the Lambda function
5. Configured the required IAM permissions
6. Used Lambda to process the required data
7. Generated a report
8. Stored the generated report in an S3 bucket
9. Waited for the scheduled execution
10. Verified the generated report in S3

## 📊 Testing

For testing purposes, I configured:

```text
Schedule:
Every 2 Minutes

Trigger:
Lambda Function

Output:
Generated Report → S3 Bucket
```

After the scheduled interval, EventBridge automatically triggered the Lambda function and the report-generation workflow executed.

## 💡 Key Learning

I learned that EventBridge can be used to **automate tasks based on schedules**, without manually running the process.

The main concept I learned was:

> **EventBridge Scheduler → Lambda → Process Data → Generate Report → Store in S3**

I also understood how EventBridge can be integrated with existing serverless architectures.

## 🎯 Project Outcome

Successfully extended my previous **S3 + Lambda + DynamoDB serverless project** by adding an **Amazon EventBridge scheduled workflow**.

For testing, I configured EventBridge to run every **2 minutes**, automatically trigger the Lambda function and generate a report that was stored in S3.

This hands-on project gave me practical experience with:

* Amazon EventBridge
* EventBridge Scheduler
* Scheduled Automation
* AWS Lambda
* Amazon S3
* Amazon DynamoDB
* IAM Permissions
* Serverless Architecture
* Event-Driven Architecture
* Automated Report Generation
