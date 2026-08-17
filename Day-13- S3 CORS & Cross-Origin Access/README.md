# Day 13 – S3 CORS & Cross-Origin Access 🌐🔐

## 📅 Topic

**Amazon S3 CORS Configuration**

## 📌 What I Learned

In this session, I learned about **CORS (Cross-Origin Resource Sharing)** and how it controls browser-based requests between different origins.

I performed a hands-on project using two S3 buckets and observed a CORS error when one webpage attempted to access a resource from another S3 bucket.

## 🪣 Project Setup

I created two S3 buckets:

```text id="qk4x2e"
Source S3 Bucket
      │
      └── Source HTML Page

Destination S3 Bucket
      │
      └── Destination HTML Page
```

The Source Bucket contained an HTML page with a button.

The Destination Bucket contained another HTML page that I wanted to access from the Source webpage.

## 🏗️ Project Flow

```text id="qf0y7c"
Source HTML Page
       │
       │ Button Click
       ↓
Cross-Origin Request
       │
       ↓
Destination S3 Bucket
       │
       ↓
Destination HTML Page
```

## ⚠️ CORS Error

Initially, when I clicked the button from the Source HTML page, the browser generated a **CORS error**.

The browser blocked the request because the Source and Destination were different origins and the required cross-origin permission was not configured.

```text id="z8m6r1"
Source Website
      │
      │ Cross-Origin Request
      ↓
Destination S3
      │
      ↓
❌ CORS Error
```

## 🔐 What is CORS?

**CORS stands for Cross-Origin Resource Sharing.**

It is a browser security mechanism that controls whether a webpage from one origin can access resources from another origin.

Simple concept:

> **CORS controls which cross-origin browser requests are allowed.**

## 🛠️ How I Resolved the CORS Error

To resolve the issue, I went to the **Destination S3 Bucket** and configured the required **CORS rules**.

I allowed the required origin and HTTP method for the request.

Conceptually:

```text id="8n2xk4"
Source Website
      │
      │ Request
      ↓
Destination S3
      │
      ↓
CORS Configuration
      │
      ↓
✅ Request Allowed
```

I also ensured that the required bucket/object access permissions were configured.

## 🔄 Before and After

### Before CORS Configuration

```text id="s3l0r2"
Source HTML
    ↓
Button Click
    ↓
Destination Request
    ↓
❌ CORS Error
```

### After CORS Configuration

```text id="k8q4t1"
Source HTML
    ↓
Button Click
    ↓
Destination Request
    ↓
CORS Configuration
    ↓
✅ Request Allowed
    ↓
Destination HTML Page
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created a Source S3 Bucket
2. Created a Destination S3 Bucket
3. Created an HTML page in the Source Bucket
4. Created an HTML page in the Destination Bucket
5. Added a button to the Source HTML page
6. Sent a request to the Destination resource
7. Observed the CORS error
8. Identified the cross-origin access issue
9. Configured CORS on the Destination S3 Bucket
10. Configured the required bucket/object access permissions
11. Tested the request again
12. Successfully accessed the Destination HTML page

## 💡 Key Learning

This project helped me understand how browsers protect users from unauthorized cross-origin requests and how S3 CORS configuration can be used to allow legitimate cross-origin access.

```text id="p6b2q7"
CORS
 ↓
Cross-Origin Request Control
 ↓
Source Website
 ↓
Destination S3 Resource
```

## 🎯 Project Outcome

Successfully identified and resolved a **CORS error** while accessing a resource from a different S3 origin.

This hands-on project gave me practical experience with:

* Amazon S3
* S3 Buckets
* HTML
* Cross-Origin Requests
* CORS
* Bucket Policies
* Object Access
* Browser Security
* S3 Access Configuration

## 📝 Important Difference

**S3 Replication and S3 CORS are two different concepts.**

| Concept        | Purpose                                      |
| -------------- | -------------------------------------------- |
| S3 Replication | Copies objects from one S3 bucket to another |
| S3 CORS        | Controls browser-based cross-origin requests |
