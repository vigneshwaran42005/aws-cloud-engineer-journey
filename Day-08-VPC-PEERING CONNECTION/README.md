# Day 08 – VPC Peering Connection with IIS Web Server 🔗🌐

## 📅 Topic

**VPC Peering Connection – VPC-to-VPC IIS Web Server Communication**

## 📌 Project Overview

In this hands-on project, I created **two separate VPCs** and deployed a Windows EC2 instance with an IIS web server in each VPC.

I then established a **VPC Peering Connection** between the two VPCs and configured the required routing and security rules.

Finally, I accessed the **IIS web page hosted in VPC 2 from the EC2 instance in VPC 1 using the private IP address and HTTP port**.

## 🏗️ Project Architecture

```text
                         AWS Region
                              │
              ┌───────────────┴───────────────┐
              │                               │
           VPC 1                           VPC 2
        10.0.0.0/16                     20.0.0.0/16
              │                               │
              │                               │
        Windows EC2                      Windows EC2
              │                               │
          IIS Server                      IIS Server
              │                               │
        HTML Web Page                   HTML Web Page
              │                               │
              └──── VPC Peering Connection ───┘
                              │
                       Private Communication
```

## 🖥️ VPC 1 – Source VPC

In **VPC 1**, I:

1. Created a VPC
2. Created a subnet
3. Launched a Windows EC2 instance
4. Connected to the instance using RDP
5. Installed IIS Web Server
6. Created a custom HTML web page
7. Verified the IIS website locally

Example:

```text
VPC 1
  ↓
Windows EC2
  ↓
IIS
  ↓
Custom HTML Page
```

## 🖥️ VPC 2 – Destination VPC

In **VPC 2**, I created another Windows EC2 instance and configured IIS in the same way.

```text
VPC 2
  ↓
Windows EC2
  ↓
IIS
  ↓
Custom HTML Page
```

The HTML page in VPC 2 was used to verify communication from VPC 1.

## 🔗 VPC Peering Connection

I created a **VPC Peering Connection** between VPC 1 and VPC 2.

```text
VPC 1
10.0.0.0/16
    │
    │
    │ VPC Peering
    │
    ↓
VPC 2
20.0.0.0/16
```

The two VPCs had **non-overlapping CIDR ranges**.

## 🛣️ Route Table Configuration

I configured routes in both VPCs so that traffic destined for the other VPC was sent through the VPC Peering Connection.

### VPC 1 Route Table

```text
Destination: 20.0.0.0/16
Target:      VPC Peering Connection
```

### VPC 2 Route Table

```text
Destination: 10.0.0.0/16
Target:      VPC Peering Connection
```

This enabled private communication between resources in the two VPCs.

## 🔐 Security Group Configuration

I configured the Security Groups to allow the required traffic between the EC2 instances.

For the IIS web server in VPC 2:

```text
Protocol: TCP
Port:     80 (HTTP)
Source:   VPC 1 private CIDR
```

This allowed the EC2 instance in VPC 1 to access the IIS web server in VPC 2.

## 🌐 Testing the Connection

After configuring the VPC Peering Connection, Route Tables and Security Groups, I tested the connection from the **VPC 1 EC2 instance**.

From the source EC2 instance, I accessed the IIS web server in VPC 2 using the **private IP address of the VPC 2 EC2 instance** and HTTP port 80.

```text
VPC 1 EC2
   │
   │ HTTP : 80
   │
   ↓
VPC Peering
   │
   ↓
VPC 2 EC2
   │
   ↓
IIS Web Server
   │
   ↓
HTML Web Page
```

### ✅ Result

The **HTML web page hosted on the IIS server in VPC 2 was successfully accessed from the EC2 instance in VPC 1** through the VPC Peering Connection.

This confirmed that private communication between the two VPCs was working successfully.

## 🧪 Hands-on Steps

1. Created VPC 1
2. Created VPC 2
3. Configured non-overlapping CIDR blocks
4. Created subnets
5. Launched Windows EC2 in VPC 1
6. Launched Windows EC2 in VPC 2
7. Connected to both EC2 instances using RDP
8. Installed IIS on both Windows servers
9. Created custom HTML pages
10. Created VPC Peering Connection
11. Accepted the peering request
12. Updated VPC 1 Route Table
13. Updated VPC 2 Route Table
14. Configured Security Groups
15. Allowed HTTP traffic on port 80
16. Tested communication using the private IP address
17. Successfully accessed the VPC 2 IIS web page from VPC 1

## 💡 Key Learning

This project helped me understand that creating a VPC Peering Connection alone is not sufficient.

For successful VPC-to-VPC communication, the following are required:

```text
VPC Peering
      +
Correct Route Tables
      +
Security Group Rules
      +
Non-overlapping CIDRs
      +
Application Port Access
```

I gained practical experience in connecting two isolated VPC networks and accessing an **IIS-hosted web application across VPCs using private networking**.

## 🎯 Project Outcome

Successfully established **private communication between two VPCs** and accessed an **IIS web server hosted in VPC 2 from an EC2 instance in VPC 1** using VPC Peering.

This project demonstrated practical knowledge of:

* Amazon VPC
* VPC Peering
* Windows EC2
* IIS Web Server
* HTML
* Route Tables
* Security Groups
* Private IP Communication
* HTTP Port 80
* RDP
* VPC-to-VPC Networking
