# Day 06 – VPC Architecture 🌐🏗️

## 📅 Topic

**AWS VPC Architecture**

## 📌 What I Learned

In this session, I learned how to design a basic **high-availability VPC architecture** using multiple Availability Zones, public and private subnets, route tables, Internet Gateway and NAT Gateway.

A well-designed VPC separates internet-facing resources from private resources and provides controlled network communication.

## 🏗️ VPC Architecture

```text
                              Internet
                                  │
                                  ↓
                         Internet Gateway
                                  │
                    ┌─────────────┴─────────────┐
                    │          VPC              │
                    │       10.0.0.0/16         │
                    │                           │
          ┌─────────┴─────────┐   ┌─────────────┴─────────┐
          │      AZ-1         │   │        AZ-2           │
          │                   │   │                       │
          │ Public Subnet     │   │ Public Subnet         │
          │ 10.0.1.0/24       │   │ 10.0.3.0/24           │
          │      │            │   │       │               │
          │     EC2           │   │      EC2              │
          │                   │   │                       │
          │ Private Subnet    │   │ Private Subnet        │
          │ 10.0.2.0/24       │   │ 10.0.4.0/24           │
          │      │            │   │       │               │
          │     EC2           │   │      EC2              │
          │      │            │   │       │               │
          │ NAT Gateway       │   │ NAT Gateway           │
          └───────────────────┘   └───────────────────────┘
```

## 🌍 Components Used

### 1. VPC

Created a VPC with a dedicated CIDR block.

**Example:**

```text
10.0.0.0/16
```

The VPC provides the overall private network for AWS resources.

### 2. Availability Zones

Used multiple Availability Zones to improve availability and fault tolerance.

```text
VPC
 ├── AZ-1
 └── AZ-2
```

If one AZ experiences a failure, resources in another AZ can continue operating.

### 3. Public Subnets

Created public subnets in multiple AZs.

Example:

```text
AZ-1 → 10.0.1.0/24
AZ-2 → 10.0.3.0/24
```

Public subnets contain resources that require direct internet connectivity, such as internet-facing components.

### 4. Private Subnets

Created private subnets in multiple AZs.

Example:

```text
AZ-1 → 10.0.2.0/24
AZ-2 → 10.0.4.0/24
```

Private subnets are used for resources that should not be directly accessible from the internet.

### 5. Internet Gateway

Attached an Internet Gateway to the VPC.

```text
Public Subnet
      ↓
Route Table
      ↓
Internet Gateway
      ↓
Internet
```

### 6. NAT Gateway

Used NAT Gateway to provide outbound internet access to resources in private subnets.

```text
Private EC2
     ↓
Private Route Table
     ↓
NAT Gateway
     ↓
Internet Gateway
     ↓
Internet
```

## 🛣️ Route Tables

### Public Route Table

```text
Destination       Target

10.0.0.0/16       local
0.0.0.0/0         Internet Gateway
```

The public route table provides a route from the public subnet to the Internet Gateway.

### Private Route Table

```text
Destination       Target

10.0.0.0/16       local
0.0.0.0/0         NAT Gateway
```

The private route table sends outbound internet traffic through the NAT Gateway.

## 🔐 Security

Security Groups were used to control traffic to EC2 instances.

The architecture follows the principle of keeping private resources inaccessible directly from the internet.

```text
Internet
   ↓
Public Resources
   ↓
Private Resources
```

## 🧪 Hands-on Practice

During this session, I practiced:

1. Designing a VPC architecture
2. Creating a VPC with CIDR `10.0.0.0/16`
3. Creating multiple Availability Zones
4. Creating public subnets
5. Creating private subnets
6. Creating and configuring route tables
7. Attaching an Internet Gateway
8. Configuring NAT Gateway
9. Associating subnets with route tables
10. Understanding traffic flow between public and private resources
11. Launching EC2 resources in the appropriate subnets

## 🔄 Traffic Flow

### Public Resource

```text
Internet
   ↓
Internet Gateway
   ↓
Public Route Table
   ↓
Public Subnet
   ↓
EC2
```

### Private Resource

```text
Private EC2
   ↓
Private Route Table
   ↓
NAT Gateway
   ↓
Internet Gateway
   ↓
Internet
```

## 💡 Key Learning

I learned how to design a **multi-AZ VPC architecture** with separate public and private subnets.

I also understood how **Route Tables, Internet Gateway and NAT Gateway** work together to control traffic flow and provide secure network connectivity.

### Important Architecture Principle

> **Public resources should be placed in public subnets, while application and database resources should generally be placed in private subnets.**

## 🎯 AWS Focus

The main focus of Day 06 was designing and understanding a **secure, scalable and highly available AWS VPC architecture using multiple Availability Zones and public/private subnets.**
