# Day 23 – EKS, EFS & Elastic Beanstalk ☁️🚀

## 📅 Topics

* Amazon EKS
* Amazon EFS
* AWS Elastic Beanstalk

---

# ☸️ Amazon EKS

## 📌 What is Amazon EKS?

**Amazon EKS (Elastic Kubernetes Service)** is a managed AWS service used to run and manage **Kubernetes clusters**.

Kubernetes is a container orchestration platform used to deploy, manage, scale and operate containerized applications.

With Amazon EKS, AWS manages the Kubernetes control plane while we can run our containerized workloads on the cluster.

### Simple Concept

```text
Containerized Application
          ↓
      Kubernetes
          ↓
        EKS
          ↓
    AWS Infrastructure
```

## 🎯 Why EKS?

EKS can be used for:

* Container orchestration
* Application deployment
* Container scaling
* High availability
* Kubernetes-based workloads
* Managing containerized applications

### Basic EKS Architecture

```text
                    Amazon EKS
                        │
              Kubernetes Cluster
                        │
          ┌─────────────┴─────────────┐
          ↓                           ↓
      Worker Node                 Worker Node
          │                           │
       Pod / App                   Pod / App
```

---

# 📂 Amazon EFS – Hands-on Project

## 📌 What is Amazon EFS?

**Amazon EFS (Elastic File System)** is a managed, scalable file storage service that can be mounted by multiple EC2 instances.

This allows multiple Linux EC2 instances to access the same shared file system.

## 🏗️ Project Architecture

For my hands-on practice, I created **two Linux EC2 instances** and mounted the same EFS file system on both servers.

```text
                     Amazon EFS
                         │
              ┌──────────┴──────────┐
              │                     │
              ↓                     ↓
        Linux EC2-1            Linux EC2-2
              │                     │
          EFS Mount              EFS Mount
              │                     │
              └──────────┬──────────┘
                         │
                  Shared File System
```

## 🧪 Hands-on Practice

I performed the following steps:

1. Created an EFS file system
2. Created two Linux EC2 instances
3. Configured the required networking and Security Groups
4. Mounted the EFS file system on Linux EC2-1
5. Mounted the same EFS file system on Linux EC2-2
6. Accessed the EFS mount directory from EC2-1
7. Created a test file
8. Checked the same EFS directory from EC2-2
9. Verified that the same test file was available on EC2-2

## 🔄 EFS Testing

The test demonstrated shared storage.

```text
Linux EC2-1
     │
     ↓
EFS Mount
     │
     ↓
Create test.txt
     │
     ↓
Amazon EFS
     │
     ↓
Linux EC2-2
     │
     ↓
test.txt
```

When I created a file from the first Linux server, I was able to see the same file from the second Linux server because both EC2 instances were accessing the **same EFS file system**.

## 💡 Key Learning

The important concept I learned from this project was:

> **EFS provides shared file storage that can be mounted and accessed by multiple EC2 instances.**

```text
EC2-1 ──┐
        ├──→ EFS ←── Shared Storage
EC2-2 ──┘
```

---

# 🌱 AWS Elastic Beanstalk

## 📌 What is Elastic Beanstalk?

**AWS Elastic Beanstalk** is a managed application deployment service that makes it easier to deploy and run applications on AWS.

Instead of manually configuring all the underlying infrastructure, we provide our application and Elastic Beanstalk manages much of the deployment and environment configuration.

## 🏗️ Elastic Beanstalk Concept

```text
Application Code
       ↓
Elastic Beanstalk
       ↓
Application Environment
       ↓
AWS Resources
       ↓
Running Application
```

Depending on the environment configuration, Elastic Beanstalk can provision and manage resources such as:

* EC2
* Auto Scaling
* Load Balancing
* Security Groups
* Application environment configuration

## 🧪 Hands-on Practice

I also explored Elastic Beanstalk by:

1. Opened Elastic Beanstalk
2. Created an application
3. Created an application environment
4. Selected the required platform/runtime
5. Configured the environment settings
6. Explored the deployment configuration
7. Understood how Elastic Beanstalk manages the application environment

## 💡 Easy Way to Understand

Without Elastic Beanstalk:

```text
Developer
   ↓
Manually Configure
   ↓
EC2
   ↓
Load Balancer
   ↓
Auto Scaling
   ↓
Application
```

With Elastic Beanstalk:

```text
Developer
   ↓
Application Code
   ↓
Elastic Beanstalk
   ↓
Application Environment
   ↓
Running Application
```

## 🎯 Key Learning

I learned that Elastic Beanstalk provides a simpler way to **deploy and manage applications without manually handling every underlying infrastructure component**.

---

# 🔄 Day 23 – Overall Learning

```text
EKS
 ↓
Kubernetes
 ↓
Container Orchestration


EFS
 ↓
Shared File Storage
 ↓
Multiple EC2 Instances
 ↓
Same Files


Elastic Beanstalk
 ↓
Application Deployment
 ↓
Managed Environment
 ↓
Running Application
```

## 🧪 Hands-on Outcome

The main practical exercise was the **EFS shared-storage project**.

I successfully mounted the same EFS file system on two Linux EC2 instances and verified that a file created from one EC2 instance was visible from the other EC2 instance.

I also learned the fundamental concepts of **Amazon EKS** and **AWS Elastic Beanstalk**.

## 🚀 AWS Concepts Practiced

* Amazon EKS
* Kubernetes
* Container Orchestration
* Amazon EFS
* Shared File Storage
* Linux EC2
* EFS Mount
* Security Groups
* AWS Elastic Beanstalk
* Application Deployment
* Application Environments
* Managed AWS Services
