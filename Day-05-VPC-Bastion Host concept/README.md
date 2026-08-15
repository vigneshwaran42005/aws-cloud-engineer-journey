# Day 05 – VPC Bastion Host Using Windows EC2 🖥️🔐

## 📅 Topic

**VPC Bastion Host – Secure Access to Private Windows EC2**

## 📌 What I Learned

A **Bastion Host** is a server placed in a public subnet that acts as a secure entry point to access resources located in a private subnet.

Instead of allowing direct internet access to a private EC2 instance, we connect to the Bastion Host first and then access the private server through it.

## 🏗️ Bastion Host Architecture

```text
                    Internet
                       │
                       │ RDP
                       ↓
              Public Subnet
              ┌────────────────┐
              │ Windows EC2    │
              │ Bastion Host   │
              └───────┬────────┘
                      │
                      │ RDP
                      ↓
              Private Subnet
              ┌────────────────┐
              │ Windows EC2    │
              │ Private Server │
              └────────────────┘
```

## 🪟 Windows RDP Access

For this hands-on practice, I used **Windows EC2 instances** and **Remote Desktop Protocol (RDP)**.

### Connection Flow

```text
My Windows PC
      │
      │ RDP
      ↓
Public Windows EC2
(Bastion Host)
      │
      │ RDP
      ↓
Private Windows EC2
```

The private Windows EC2 instance does not need a public IP address.

## 🔐 Security Group Configuration

### Bastion Host Security Group

Allow:

```text
Inbound:
RDP - TCP 3389
Source: My IP Address
```

This restricts RDP access to the Bastion Host.

### Private Windows EC2 Security Group

Allow:

```text
Inbound:
RDP - TCP 3389
Source: Bastion Host Security Group
```

This is more secure than allowing RDP from `0.0.0.0/0`.

## 🧪 Hands-on Practice

During this session, I practiced:

1. Created a VPC
2. Created a public subnet
3. Created a private subnet
4. Created an Internet Gateway
5. Configured public and private route tables
6. Launched a Windows EC2 instance in the public subnet
7. Used the public Windows EC2 as a Bastion Host
8. Connected to the Bastion Host using RDP
9. Launched a Windows EC2 instance in the private subnet
10. Connected from the Bastion Host to the private Windows EC2 using RDP
11. Configured Security Groups for controlled RDP access

## 🔒 Why Use a Bastion Host?

Without a Bastion Host:

```text
Internet
   │
   │ RDP
   ↓
Private EC2 ❌
```

With a Bastion Host:

```text
Internet
   │
   │ RDP
   ↓
Bastion Host
   │
   │ RDP
   ↓
Private EC2 ✅
```

The private server remains inaccessible directly from the public internet.

## 💡 Key Learning

I learned how a Bastion Host provides a controlled access point for managing private servers.

I also learned how to use **Windows RDP, Security Groups, Public/Private Subnets and Route Tables** to securely access a private Windows EC2 instance.

### Important Security Concept

> **Do not expose the private server directly to the internet. Use a Bastion Host as a controlled administrative entry point.**

## 🎯 AWS Focus

The main focus of this session was understanding **Bastion Host architecture and secure Windows EC2 access using RDP** in a VPC environment.
