# Day 20 – Amazon RDS & PostgreSQL 🗄️🐘

## 📅 Topic

**Amazon RDS – Relational Database Service**

## 📌 What I Learned

In this session, I learned about **Amazon RDS (Relational Database Service)** and how to create and manage a relational database on AWS.

Amazon RDS is a **managed relational database service**. AWS handles many administrative tasks such as infrastructure provisioning, backups, patching and maintenance, allowing us to focus on the database and application.

## 🗄️ What is Amazon RDS?

Amazon RDS makes it easier to set up, operate and scale relational databases in AWS.

RDS supports multiple database engines, including:

* PostgreSQL
* MySQL
* MariaDB
* Oracle
* Microsoft SQL Server
* Amazon Aurora

For my hands-on practice, I mainly worked with **PostgreSQL**.

## 🏗️ RDS Concept

Traditional database setup:

```text id="m8v1pa"
Server
  ↓
Install Database
  ↓
Configure Database
  ↓
Manage Updates
  ↓
Manage Backups
  ↓
Manage Maintenance
```

With Amazon RDS:

```text id="f4s2kw"
AWS RDS
   ↓
Select Database Engine
   ↓
Configure Instance
   ↓
Create Database
   ↓
Connect & Use
```

AWS manages much of the underlying database infrastructure.

## 🐘 PostgreSQL

For this hands-on session, I selected **PostgreSQL** as the RDS database engine.

PostgreSQL is an open-source relational database management system that uses SQL for querying and managing structured data.

```text id="9q3p5j"
Amazon RDS
     ↓
PostgreSQL
     ↓
Database
     ↓
Tables
     ↓
Rows & Columns
```

## ⚙️ RDS Database Creation

I practiced creating an RDS database from the AWS Management Console.

During the creation process, I explored and configured settings such as:

* Database engine
* PostgreSQL version
* DB instance configuration
* Credentials
* Master username
* Master password
* Storage
* Connectivity
* VPC
* Subnet configuration
* Security Group
* Database port

I also reviewed the available configuration options and selected lower-cost settings suitable for **learning and testing**.

## 💰 Cost Optimization During Practice

Since this was a learning environment, I explored the configuration options and selected the smallest practical resources available for the exercise to minimize unnecessary AWS charges.

> **Important:** RDS is a paid service, and the actual cost depends on the selected instance class, storage, engine, region, backup configuration and running time.

For practice environments, resources should be stopped or deleted when they are no longer required, while also checking whether the selected RDS configuration supports stopping and what charges continue to apply.

## 🌐 RDS Connectivity

After creating the RDS PostgreSQL instance, I obtained the database **endpoint** and configured the required connectivity settings.

The basic connection flow was:

```text id="9j1s7x"
Local Computer
      ↓
Database Client / pgAdmin
      ↓
RDS Endpoint
      ↓
PostgreSQL
      ↓
RDS Database
```

## 🔐 Master Credentials

During RDS creation, I configured:

```text id="z9y4rm"
Master Username
Master Password
```

These credentials were then used to authenticate to the PostgreSQL database from the database client.

## 🖥️ PostgreSQL Client / pgAdmin

I downloaded and installed a PostgreSQL database management tool such as **pgAdmin** on my local computer.

I then used the RDS connection details to connect to the PostgreSQL database.

The connection required details such as:

```text id="6v3b9c"
Host / Endpoint → RDS Endpoint
Port            → PostgreSQL Port
Username        → Master Username
Password        → Master Password
Database        → PostgreSQL Database
```

## 🔗 Connection Flow

```text id="9v8r4w"
Local PC
   │
   ↓
pgAdmin
   │
   │ RDS Endpoint + Credentials
   ↓
Amazon RDS
   │
   ↓
PostgreSQL Database
```

## 🗃️ Creating a Database Table

After successfully connecting to the RDS PostgreSQL instance, I practiced creating SQL tables.

Example:

```sql id="h4e8qx"
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(150),
    role VARCHAR(100)
);
```

I also practiced working with SQL commands to manage and interact with the database.

Example:

```sql id="q0z7vk"
SELECT * FROM employees;
```

## 🧪 Hands-on Practice

During this session, I practiced:

1. Opened Amazon RDS
2. Selected PostgreSQL
3. Explored RDS database configuration
4. Selected the required database version
5. Configured database credentials
6. Configured the master username
7. Configured the master password
8. Configured instance and storage settings
9. Configured VPC and connectivity
10. Configured the required Security Group
11. Created the RDS PostgreSQL instance
12. Obtained the RDS endpoint
13. Installed PostgreSQL/pgAdmin database client
14. Connected to RDS using the master credentials
15. Created a SQL database/table
16. Inserted and queried data
17. Verified the database operations from the client

## 💡 Key Learning

The main concept I learned was:

> **Amazon RDS provides a managed environment for running relational databases without manually managing the underlying database server infrastructure.**

I also learned how a locally installed database client can connect to an RDS PostgreSQL database using the RDS endpoint, credentials and appropriate network/security configuration.

## 🔄 Complete Project Flow

```text id="k3r0ph"
AWS Console
     ↓
Amazon RDS
     ↓
PostgreSQL
     ↓
Configure Database
     ↓
Create RDS Instance
     ↓
Get RDS Endpoint
     ↓
Configure Connectivity
     ↓
pgAdmin / PostgreSQL Client
     ↓
Connect using Credentials
     ↓
Create SQL Tables
     ↓
Insert / Query Data
```

## 🎯 Project Outcome

Successfully created an **Amazon RDS PostgreSQL database**, configured the required connectivity and connected to the database using a PostgreSQL client.

I also practiced creating SQL tables and performing basic database operations through the RDS PostgreSQL instance.

## 🚀 AWS Concepts Practiced

* Amazon RDS
* Relational Databases
* PostgreSQL
* Amazon Aurora
* RDS Database Engines
* DB Instance
* Database Endpoint
* Master Username & Password
* VPC Connectivity
* Security Groups
* Database Port
* pgAdmin / PostgreSQL Client
* SQL Tables
* SQL Queries
* RDS Cost Optimization
* Managed Database Services
