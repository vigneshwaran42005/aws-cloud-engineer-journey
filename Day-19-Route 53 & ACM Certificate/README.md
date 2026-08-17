# Day 19 – Amazon Route 53 & ACM Certificate 🌐🔐

## 📅 Topic

**Amazon Route 53 – DNS & Domain Management**

**AWS Certificate Manager (ACM) – SSL/TLS Certificate**

## 📌 What I Learned

In this session, I learned about **Amazon Route 53**, AWS's highly available and scalable **Domain Name System (DNS) web service**.

I learned how DNS converts a human-friendly domain name into the destination required to reach an application.

I also learned how a custom domain purchased from a domain registrar such as **GoDaddy** can be connected to an AWS-hosted application using DNS records.

## 🌍 Why Do We Need a Domain Name?

Applications and websites are accessed through network addresses and service endpoints, but remembering technical addresses is difficult for users.

For example:

```text
Technical Address
       ↓
192.0.2.10
```

Instead of asking users to remember an IP address, we can use a user-friendly domain name:

```text
example.com
```

The DNS system maps the domain name to the appropriate destination.

```text
User
 ↓
example.com
 ↓
DNS
 ↓
Application
```

## 🌐 What is Amazon Route 53?

Amazon Route 53 is an AWS **DNS service** used to route users to applications and resources.

It can be used for:

* DNS management
* Domain name resolution
* Routing internet traffic
* Health checks
* Connecting domains with AWS resources

## 🏷️ Domain Registration & Route 53

For this learning exercise, I understood the concept of purchasing a domain from a domain registrar such as **GoDaddy**.

The domain can then be configured to use DNS records managed through Route 53.

Conceptually:

```text
Domain Registrar
      ↓
Purchase Domain
      ↓
Route 53 Hosted Zone
      ↓
DNS Records
      ↓
AWS Application
```

The domain registration and DNS hosting are separate concepts.

## 🪣 Route 53 with S3 Static Website

I connected the Route 53 DNS concept with my previous **S3 Static Website Hosting** project.

The overall flow is:

```text
User
  ↓
Custom Domain
  ↓
Route 53
  ↓
S3 Static Website
  ↓
HTML Page
```

Instead of users remembering the S3 website endpoint, they can access the application using a custom domain name.

## 📝 DNS Records

I learned about different DNS record types, especially **A Records and CNAME Records**.

### 1. A Record

An **A Record** maps a domain name to an **IPv4 address**.

Example:

```text
example.com
      ↓
A Record
      ↓
192.0.2.10
```

The A record is used when the destination is an IPv4 address.

### 2. CNAME Record

A **CNAME (Canonical Name) Record** maps one domain name to another domain name.

Example:

```text
www.example.com
       ↓
CNAME
       ↓
example.com
```

CNAME is useful when one hostname needs to point to another hostname.

## 💡 Easy Way to Remember

```text
A Record
→ Domain → IPv4 Address

CNAME
→ Domain → Another Domain Name
```

## 🔐 AWS Certificate Manager (ACM)

I also learned about **AWS Certificate Manager (ACM)**.

ACM is used to provision, manage and deploy **SSL/TLS certificates** for AWS services and applications.

A certificate allows a website to use **HTTPS** and provides encrypted communication between the client and the application.

### HTTP vs HTTPS

```text
HTTP
 ↓
Unencrypted communication

HTTPS
 ↓
Encrypted communication
 ↓
SSL/TLS Certificate
```

## 🔒 Why HTTPS?

HTTP traffic is not encrypted by TLS.

HTTPS uses **TLS encryption** to protect data exchanged between the user and the application.

Therefore, for a production website, HTTPS is important for secure communication.

## 📜 ACM Certificate Request

I learned how to request an SSL/TLS certificate using AWS Certificate Manager.

The general process is:

```text
ACM
 ↓
Request Certificate
 ↓
Enter Domain Name
 ↓
Choose DNS Validation
 ↓
Receive CNAME Record
 ↓
Add CNAME to DNS
 ↓
Domain Validation
 ↓
Certificate Issued
```

## 🔗 DNS Validation using CNAME

During ACM certificate validation, ACM provides a **CNAME name and CNAME value**.

These values are added to the domain's DNS configuration.

```text
ACM
 │
 │ CNAME Validation Record
 ↓
Route 53 DNS
 │
 ↓
Domain Validation
 │
 ↓
Certificate Issued
```

This allows ACM to verify that we control the domain.

## 🧪 Hands-on / Concepts Practiced

During this session, I practiced and understood:

1. What DNS is
2. What Amazon Route 53 is
3. Domain names and DNS resolution
4. Domain registration using a registrar such as GoDaddy
5. Route 53 Hosted Zones
6. DNS Records
7. A Records
8. CNAME Records
9. Connecting a custom domain with an AWS-hosted application
10. Route 53 with S3 Static Website Hosting
11. HTTP vs HTTPS
12. AWS Certificate Manager
13. SSL/TLS certificates
14. ACM certificate request
15. DNS validation
16. ACM CNAME validation records

## 🔄 Complete Concept Flow

```text
                 User
                   │
                   ↓
            Custom Domain
            example.com
                   │
                   ↓
               Route 53
                   │
            DNS Resolution
                   │
          ┌────────┴────────┐
          │                 │
          ↓                 ↓
     AWS Application    S3 Website
                            │
                            ↓
                       HTML Page
```

### HTTPS Flow

```text
User
  ↓
https://example.com
  ↓
Route 53
  ↓
AWS Application
  ↓
ACM SSL/TLS Certificate
  ↓
Secure HTTPS Connection
```

## 💡 Key Learning

The main concepts I learned were:

> **Route 53 → DNS and traffic routing**

> **A Record → Domain to IPv4 address**

> **CNAME → Domain to another domain name**

> **ACM → SSL/TLS certificate management**

> **DNS Validation → CNAME record used to validate domain ownership**

## 🎯 Project / Practical Outcome

I gained practical understanding of how a **custom domain can be connected to an AWS-hosted application** using Route 53 and how HTTPS can be enabled using an ACM SSL/TLS certificate.

This helped me understand the complete relationship between:

```text
Domain
   ↓
DNS
   ↓
Route 53
   ↓
AWS Application
   ↓
ACM Certificate
   ↓
HTTPS
```

## 🚀 AWS Concepts Practiced

* Amazon Route 53
* DNS
* Hosted Zones
* A Records
* CNAME Records
* Domain Names
* Domain Registration
* S3 Static Website Hosting
* AWS Certificate Manager (ACM)
* SSL/TLS
* HTTPS
* DNS Validation
