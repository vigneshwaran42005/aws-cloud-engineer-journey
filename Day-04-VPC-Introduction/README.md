# Day 04 – VPC Introduction 🌐

## 📅 Topic

**Amazon VPC – Introduction and Networking Basics**

## 📌 What I Learned

Amazon Virtual Private Cloud (VPC) allows us to create a logically isolated virtual network within AWS.

A VPC gives us control over:

* IP address ranges
* Subnets
* Routing
* Internet connectivity
* Network security
* Availability Zones

## 🌍 AWS Region

An **AWS Region** is a geographical location where AWS provides cloud infrastructure.

Example:

```text
us-east-1
```

A Region contains multiple Availability Zones.

```text
AWS Region: us-east-1
        │
        ├── Availability Zone 1
        ├── Availability Zone 2
        └── Availability Zone 3
```

## 🏢 Availability Zone (AZ)

An **Availability Zone** is an isolated location within an AWS Region.

AZs are used to build highly available applications.

Example:

```text
Region
  │
  ├── AZ-1
  │    └── Subnets
  │
  └── AZ-2
       └── Subnets
```

If one Availability Zone experiences a failure, resources in another AZ can continue to operate.

## 🌐 VPC

A **VPC (Virtual Private Cloud)** is a logically isolated network in AWS where we can launch resources such as EC2 instances, databases and other services.

Example:

```text
VPC
CIDR: 10.0.0.0/16
```

The VPC CIDR defines the IP address range available inside the VPC.

## 📦 Subnet

A **Subnet** is a smaller network range created inside a VPC.

Subnets are associated with a specific Availability Zone.

Example:

```text
VPC: 10.0.0.0/16
       │
       ├── Public Subnet
       │   10.0.1.0/24
       │
       └── Private Subnet
           10.0.2.0/24
```

### Public Subnet

A subnet is considered public when its route table has a route to an **Internet Gateway**.

### Private Subnet

A private subnet does not have a direct route to an Internet Gateway.

Private resources can use a **NAT Gateway** for outbound internet connectivity when required.

## 🛣️ Route Table

A Route Table controls where network traffic is directed.

Example:

```text
Destination       Target

10.0.0.0/16       local
0.0.0.0/0         Internet Gateway
```

The `0.0.0.0/0` route represents traffic destined for the internet.

## 🌐 Internet Gateway (IGW)

An **Internet Gateway** allows communication between resources in a VPC and the public internet.

For a public subnet:

```text
EC2
 ↓
Route Table
 ↓
Internet Gateway
 ↓
Internet
```

The Internet Gateway must be attached to the VPC.

## 🔄 NAT Gateway

A **NAT Gateway (Network Address Translation Gateway)** allows resources in a private subnet to access the internet for outbound communication without allowing unsolicited inbound internet connections.

Example:

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

### Important Difference

**Internet Gateway:**

> Provides direct internet connectivity for resources in a public subnet.

**NAT Gateway:**

> Allows resources in a private subnet to initiate outbound internet connections.

## 🏗️ VPC Architecture

```text
                         Internet
                            │
                            ↓
                   Internet Gateway
                            │
             ┌──────────────┴──────────────┐
             │           VPC               │
             │        10.0.0.0/16          │
             │                             │
             │  Public Subnet              │
             │      │                      │
             │     EC2                     │
             │                             │
             │  Private Subnet             │
             │      │                      │
             │     EC2                     │
             │      │                      │
             │  NAT Gateway                │
             └─────────────────────────────┘
```

## 🧪 Hands-on Practice

During this session, I practiced the basic AWS networking setup:

1. Explored AWS Regions
2. Understood Availability Zones
3. Created a VPC
4. Configured a VPC CIDR block
5. Created public and private subnets
6. Associated subnets with Availability Zones
7. Created a Route Table
8. Configured routes
9. Created and attached an Internet Gateway
10. Learned the purpose of a NAT Gateway
11. Understood public and private subnet connectivity

## 💡 Key Learning

I learned how AWS networking is structured from **Region → Availability Zone → VPC → Subnet**.

I also understood how **Route Tables, Internet Gateway and NAT Gateway** control network connectivity inside a VPC.

### Important Concepts

```text
Region
   ↓
Availability Zone
   ↓
VPC
   ↓
Subnet
   ↓
Route Table
   ↓
IGW / NAT Gateway
```

## 🎯 AWS Focus

The main focus of Day 04 was understanding the fundamentals of **AWS VPC networking** and gaining hands-on experience with VPC, subnets, Availability Zones, Route Tables, Internet Gateway and NAT Gateway.
