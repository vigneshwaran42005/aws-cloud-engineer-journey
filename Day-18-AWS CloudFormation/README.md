# Day 18 – AWS CloudFormation ☁️🏗️

## 📅 Topic

**AWS CloudFormation – Infrastructure as Code (IaC)**

## 📌 What I Learned

In this session, I learned about **AWS CloudFormation** and the concept of **Infrastructure as Code (IaC)**.

AWS CloudFormation allows us to define AWS infrastructure using templates instead of manually creating each resource through the AWS Management Console.

With CloudFormation, infrastructure can be created, updated and managed in a repeatable way.

## 🏗️ What is AWS CloudFormation?

AWS CloudFormation is an AWS service used to provision and manage AWS resources using a template.

Instead of manually creating resources:

```text id="xk4f0n"
Console
  ↓
Create VPC
  ↓
Create Subnet
  ↓
Create EC2
  ↓
Create Security Group
```

We can define the infrastructure in a template:

```text id="y7x8ck"
CloudFormation Template
        ↓
CloudFormation Stack
        ↓
AWS Resources
```

## 💡 Infrastructure as Code

**Infrastructure as Code (IaC)** means defining infrastructure using code or configuration files.

For example, instead of manually creating an EC2 instance, we can define its configuration inside a CloudFormation template.

```text id="v9s7rb"
Template
   ↓
CloudFormation
   ↓
Resource Creation
   ↓
AWS Infrastructure
```

## 🧩 CloudFormation Template

A CloudFormation template defines the AWS resources and their configuration.

The main sections can include:

* Parameters
* Resources
* Outputs
* Mappings
* Conditions

The **Resources** section is one of the most important sections because it defines the AWS resources that CloudFormation should create.

## 📄 JSON Template

I learned how AWS infrastructure can be defined using a **JSON-formatted CloudFormation template**.

Example structure:

```json
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Resources": {
    "MyBucket": {
      "Type": "AWS::S3::Bucket"
    }
  }
}
```

This template defines an S3 bucket as a CloudFormation resource.

```text id="j5v7hf"
JSON Template
      ↓
CloudFormation
      ↓
S3 Bucket
```

## 🏗️ Visual Architecture / Designer

I also explored the visual architecture/design concept in CloudFormation.

The infrastructure can be represented visually using a canvas-style architecture view.

The resources and their relationships can be represented as a diagram, helping to understand the infrastructure architecture.

Conceptually:

```text id="x4z8pk"
          Canvas / Architecture
                  │
       ┌──────────┼──────────┐
       │          │          │
      VPC       Subnet       EC2
       │          │          │
       └──────────┴──────────┘
                  │
                  ↓
          CloudFormation
                  │
                  ↓
          AWS Infrastructure
```

This visual approach helps understand how resources are connected and how the infrastructure can be represented as code.

## 🔄 Manual Infrastructure vs CloudFormation

### Traditional Approach

```text id="q1f9da"
AWS Console
    ↓
Create VPC
    ↓
Create Subnets
    ↓
Create Security Groups
    ↓
Create EC2
    ↓
Configure Resources
```

This can become time-consuming when many resources are involved.

### CloudFormation Approach

```text id="j7c2np"
CloudFormation Template
          ↓
      Stack Creation
          ↓
   Multiple Resources
          ↓
   Complete Infrastructure
```

## 📦 CloudFormation Stack

A **CloudFormation Stack** is a collection of AWS resources created and managed together from a CloudFormation template.

Example:

```text id="w8a4qf"
CloudFormation Stack
       │
       ├── VPC
       ├── Subnet
       ├── Security Group
       └── EC2
```

Instead of managing every resource separately, the resources can be managed as part of the stack.

## 🧪 Hands-on Practice

During this session, I practiced:

1. Explored AWS CloudFormation
2. Learned the concept of Infrastructure as Code
3. Explored CloudFormation templates
4. Learned the JSON template format
5. Understood CloudFormation resources
6. Explored the visual architecture/design concept
7. Understood how infrastructure can be represented visually
8. Created/understood resource definitions using JSON
9. Learned how CloudFormation templates can provision AWS resources
10. Learned the concept of CloudFormation Stacks

## 💡 Key Learning

The main concept I learned was:

> **Instead of manually creating AWS infrastructure through the console, we can define the infrastructure as code and let CloudFormation provision the resources.**

```text id="1t8x9w"
Infrastructure
      ↓
Template
      ↓
CloudFormation Stack
      ↓
AWS Resources
```

I also learned how **JSON-formatted templates** can be used to define AWS resources and how visual architecture/design tools can help represent infrastructure.

## 🎯 Project / Practical Outcome

I gained an understanding of how AWS CloudFormation can be used to create and manage AWS infrastructure using **Infrastructure as Code**.

This helped me understand the transition from:

```text id="m0v3xw"
Manual AWS Console Configuration
             ↓
       Infrastructure as Code
             ↓
        CloudFormation
             ↓
    Repeatable Infrastructure
```

## 🚀 AWS Concepts Practiced

* AWS CloudFormation
* Infrastructure as Code (IaC)
* CloudFormation Templates
* JSON
* CloudFormation Resources
* CloudFormation Stacks
* Visual Architecture
* Automated Resource Provisioning
