# Day 09 – Application Load Balancer & Target Groups ⚖️🌐

## 📅 Topic

**Application Load Balancer (ALB) & Target Groups**

## 📌 What I Learned

In this session, I learned how an **Application Load Balancer (ALB)** distributes incoming application traffic across multiple EC2 instances.

I also learned how **Target Groups** are used to register EC2 instances and how the Load Balancer forwards requests to healthy targets.

## 🏗️ Project Architecture

I created a VPC with **four subnets distributed across Availability Zones**.

```text
                         Internet
                            │
                            ↓
                 ┌────────────────────┐
                 │ Public Load        │
                 │ Balancer           │
                 └─────────┬──────────┘
                           │
                    Public Target Group
                       /           \
                      ↓             ↓
                  Public EC2 1   Public EC2 2
                      │             │
                    IIS            IIS
                      │             │
                 HTML Page      HTML Page


                 ┌────────────────────┐
                 │ Private Load       │
                 │ Balancer           │
                 └─────────┬──────────┘
                           │
                   Private Target Group
                       /           \
                      ↓             ↓
                 Private EC2 1   Private EC2 2
                      │             │
                    IIS            IIS
                      │             │
                 HTML Page      HTML Page
```

## 🌍 VPC & Subnet Configuration

I created four subnets across multiple Availability Zones.

```text
VPC
│
├── Public Subnet 1 → AZ-1 → Public EC2 1
├── Public Subnet 2 → AZ-2 → Public EC2 2
├── Private Subnet 1 → AZ-1 → Private EC2 1
└── Private Subnet 2 → AZ-2 → Private EC2 2
```

This allowed me to practice distributing resources across Availability Zones.

## 🖥️ EC2 Configuration

I created:

### Public EC2 Instances

* Public EC2 1
* Public EC2 2

Both Windows EC2 instances were configured with **IIS Web Server**.

I created separate HTML pages on the two servers so that I could identify which EC2 instance was serving the request.

Example:

```text
Public EC2 1 → IIS → HTML Page 1

Public EC2 2 → IIS → HTML Page 2
```

### Private EC2 Instances

I also created:

* Private EC2 1
* Private EC2 2

These instances were placed inside private subnets and configured as targets for the private Target Group.

## 🎯 Target Groups

I created separate Target Groups for the public and private EC2 instances.

### Public Target Group

```text
Public Target Group
       │
       ├── Public EC2 1
       └── Public EC2 2
```

### Private Target Group

```text
Private Target Group
       │
       ├── Private EC2 1
       └── Private EC2 2
```

Target Groups also perform **health checks** to determine whether registered targets are healthy and able to receive traffic.

## ⚖️ Load Balancer Configuration

I created separate Load Balancers for the public and private architectures.

### Public Load Balancer

```text
Internet
   ↓
Public ALB
   ↓
Public Target Group
   ↓
┌───────────────┐
│               │
EC2 1         EC2 2
```

The public Load Balancer was used to receive HTTP requests from the internet and distribute them between the two public EC2 instances.

### Private Load Balancer

```text
Private ALB
     ↓
Private Target Group
     ↓
┌───────────────┐
│               │
EC2 1         EC2 2
```

The private Load Balancer was configured for resources inside the private network.

## 🔐 Security Group Configuration

I configured Security Groups to control communication between the Load Balancer and EC2 instances.

### Load Balancer Security Group

Allowed the required HTTP traffic:

```text
HTTP
Port: 80
Source: Internet / required network
```

## 🔐 Security Group Configuration

I configured Security Groups so that the EC2 instances accept application traffic **only from the Load Balancer Security Group**.

### Step 1 – Load Balancer Security Group

The Load Balancer Security Group was configured to allow the required HTTP traffic.

```text
Load Balancer Security Group
        │
        └── HTTP : 80
             Source: Required Client Traffic
```

### Step 2 – Public EC2 Security Groups

I copied the **Load Balancer Security Group ID** and used it as the source in the inbound HTTP rule of both public EC2 Security Groups.

```text
Public EC2-1 Security Group

Inbound:
HTTP
Port: 80
Source: Load Balancer Security Group
```

```text
Public EC2-2 Security Group

Inbound:
HTTP
Port: 80
Source: Load Balancer Security Group
```

### 🔄 Traffic Flow

```text
Client
  ↓
Application Load Balancer
  ↓
Load Balancer Security Group
  ↓
HTTP : 80
  ↓
┌───────────────────────┐
│                       │
EC2-1 SG              EC2-2 SG
│                       │
↓                       ↓
IIS                     IIS
│                       │
HTML Page               HTML Page
```

### 💡 Key Security Learning

Instead of allowing HTTP traffic from `0.0.0.0/0` directly to the EC2 instances, I configured the EC2 Security Groups to allow HTTP traffic **from the Load Balancer Security Group**.

This ensures that the EC2 instances receive application traffic through the Load Balancer rather than directly from arbitrary clients.

> **Load Balancer SG → EC2 SG → HTTP Port 80**

This Security Group referencing approach provides better control over communication between the Load Balancer and backend EC2 instances.

## 🌐 DNS Testing

After configuring the public Load Balancer, I copied the **Load Balancer DNS name** and opened it in my local Google Chrome browser.

Example flow:

```text
Local Chrome
     ↓
ALB DNS Name
     ↓
Public Load Balancer
     ↓
Target Group
     ↓
Healthy EC2 Target
     ↓
IIS Web Server
     ↓
HTML Page
```

## 🔄 Load Balancing Test

I created different HTML pages on the two public EC2 instances.

For example:

```text
EC2 1 → "Welcome to EC2 Server 1"

EC2 2 → "Welcome to EC2 Server 2"
```

When I accessed the Load Balancer DNS name from my browser, the request was forwarded to one of the healthy EC2 instances.

After refreshing the page, the request could be served by another healthy target.

```text
Request 1
    ↓
ALB
    ↓
EC2 1
    ↓
HTML Page 1

Request 2
    ↓
ALB
    ↓
EC2 2
    ↓
HTML Page 2
```

This demonstrated how the Load Balancer distributes incoming requests across registered healthy targets.

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created a VPC
2. Created four subnets
3. Distributed subnets across Availability Zones
4. Created two public EC2 instances
5. Created two private EC2 instances
6. Installed IIS on the Windows EC2 instances
7. Created custom HTML pages
8. Created a Public Target Group
9. Registered the two public EC2 instances
10. Created a Private Target Group
11. Registered the two private EC2 instances
12. Created a Public Application Load Balancer
13. Created a Private Load Balancer
14. Configured Load Balancer Security Groups
15. Configured EC2 Security Groups
16. Configured listeners and target groups
17. Verified target health
18. Copied the Load Balancer DNS name
19. Accessed the website using Google Chrome
20. Refreshed the page and observed requests being served by different EC2 targets

## 💡 Key Learning

This project helped me understand how an **Application Load Balancer, Target Group, EC2 instances, IIS and Security Groups** work together.

The main request flow was:

```text
Client
  ↓
Load Balancer
  ↓
Target Group
  ↓
Healthy EC2 Instance
  ↓
IIS
  ↓
HTML Web Page
```

I also learned that the Load Balancer uses **Target Groups and health checks** to determine which EC2 instances are available to receive traffic.

## 🎯 Project Outcome

Successfully configured an **Application Load Balancer with multiple EC2 instances** and verified request distribution using the Load Balancer DNS name.

By creating different HTML pages on the EC2 instances and refreshing the browser, I was able to observe the response coming from different backend servers.

## 🚀 AWS Concepts Practiced

* Amazon VPC
* Availability Zones
* Public & Private Subnets
* EC2
* Windows Server
* IIS
* Application Load Balancer
* Target Groups
* Health Checks
* Listeners
* Security Groups
* DNS
* HTTP Port 80
* Load Balancing
