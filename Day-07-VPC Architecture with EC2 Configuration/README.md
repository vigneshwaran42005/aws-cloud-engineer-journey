# Day 07 – VPC Architecture with EC2 Configuration 🖥️🌐

## 📅 Topic

**VPC Architecture with EC2 Configuration**

## 📌 What I Learned

In this session, I implemented the VPC architecture by launching and configuring **EC2 instances** inside public and private subnets.

I learned how EC2 instances communicate within a VPC and how subnet routing, Security Groups and internet connectivity affect EC2 access.

## 🏗️ Architecture

```text
                         Internet
                            │
                            ↓
                   Internet Gateway
                            │
              ┌─────────────┴─────────────┐
              │            VPC            │
              │         10.0.0.0/16       │
              │                           │
       ┌──────┴───────┐           ┌───────┴──────┐
       │     AZ-1     │           │     AZ-2     │
       │              │           │              │
       │ Public       │           │ Public       │
       │ Subnet       │           │ Subnet       │
       │              │           │              │
       │ EC2          │           │ EC2          │
       │              │           │              │
       │ Private      │           │ Private      │
       │ Subnet       │           │ Subnet       │
       │              │           │              │
       │ EC2          │           │ EC2          │
       └──────────────┘           └──────────────┘
```

## 🖥️ EC2 Configuration

I launched EC2 instances inside the VPC according to the subnet design.

### Public EC2

The public EC2 instance was launched in a **public subnet**.

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

The public EC2 can communicate with the internet when the required route, public IP and Security Group rules are configured.

### Private EC2

The private EC2 instance was launched inside a **private subnet**.

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

The private EC2 does not have direct inbound internet access.

## 🔐 Security Group Configuration

I configured Security Groups to control inbound and outbound traffic to the EC2 instances.

### Public EC2

Depending on the operating system, administrative access was configured using:

* SSH – TCP 22 for Linux
* RDP – TCP 3389 for Windows

Access should be restricted to trusted source IP addresses wherever possible.

### Private EC2

The private EC2 was configured to accept traffic only from trusted sources, such as another EC2 instance or Bastion Host Security Group.

## 🌐 IP Addressing

The EC2 instances received private IP addresses from their respective subnet CIDR ranges.

Example:

```text
VPC
10.0.0.0/16

Public Subnet
10.0.1.0/24

Private Subnet
10.0.2.0/24
```

## 🧪 Hands-on Practice

During this session, I practiced:

1. Created and configured the VPC
2. Created public and private subnets
3. Configured Availability Zones
4. Configured route tables
5. Attached the Internet Gateway
6. Configured NAT Gateway
7. Created Security Groups
8. Launched EC2 instances
9. Associated EC2 instances with the required subnets
10. Configured public and private EC2 access
11. Tested network connectivity
12. Verified EC2 communication within the VPC

## 🔄 Connectivity Flow

### Public EC2

```text
User
 ↓
Internet
 ↓
Internet Gateway
 ↓
Public Subnet
 ↓
Public EC2
```

### Private EC2

```text
Private EC2
 ↓
Private Subnet
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

I learned how to implement a VPC architecture using EC2 instances and how **subnets, route tables, Internet Gateway, NAT Gateway and Security Groups** work together.

I also understood the difference between placing EC2 instances in **public and private subnets** and how network configuration controls their connectivity.

## 🎯 AWS Focus

The main focus of Day 07 was gaining hands-on experience with **EC2 deployment inside a VPC architecture** and understanding public/private EC2 connectivity.
