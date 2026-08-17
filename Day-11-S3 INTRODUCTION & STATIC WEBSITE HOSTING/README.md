# Day 11 – Amazon S3 Introduction & Static Website Hosting 🪣🌐

## 📅 Topic

**Amazon S3 – Introduction & Static Website Hosting**

## 📌 What I Learned

Amazon S3 stands for **Simple Storage Service**.

The name **S3** comes from the three words:

> **S3 = Simple Storage Service**

Amazon S3 is an object storage service used to store and retrieve files and data from anywhere over the internet.

S3 can be used to store:

* Images
* Videos
* Documents
* HTML files
* CSS files
* JavaScript files
* Application data
* Backup files

## 🌍 S3 Bucket

An **S3 Bucket** is a container used to store objects (files and data).

```text id="y6m9m2"
S3
 │
 └── Bucket
      │
      ├── index.html
      ├── style.css
      ├── images/
      └── other files
```

### 🏷️ Bucket Name

S3 bucket names must be **globally unique**.

For example:

```text id="4evq4q"
my-website-bucket-2026
```

Another AWS account cannot create a bucket with exactly the same bucket name.

## 🌎 S3 Global Concept

S3 has a **global namespace for bucket names**, which is why bucket names must be unique across AWS.

However, when creating a bucket, the bucket's data is stored in the **AWS Region selected for that bucket**.

Example:

```text id="a9x4yu"
Bucket Name
     ↓
Global Unique Name
     ↓
Bucket Region
     ↓
Objects Stored in S3
```

## 📦 S3 Object Storage

S3 stores data as **objects** inside buckets.

An object generally consists of:

* Object data
* Object key/name
* Metadata

Example:

```text id="oj7z2k"
Bucket
  │
  ├── index.html
  ├── style.css
  └── image.jpg
```

## 🌐 Project – Static Website Hosting

As a hands-on project, I hosted a **static website using Amazon S3**.

I created an S3 bucket and uploaded an HTML webpage.

### Project Flow

```text id="5p7x8v"
HTML Page
   ↓
S3 Bucket
   ↓
Static Website Hosting
   ↓
Website Endpoint
   ↓
Google Chrome
   ↓
Web Page
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created an S3 bucket
2. Used a globally unique bucket name
3. Selected an AWS Region
4. Uploaded an `index.html` file
5. Enabled Static Website Hosting
6. Configured the index document
7. Configured the required bucket access
8. Created a Bucket Policy
9. Allowed public read access for the website objects
10. Obtained the S3 website endpoint
11. Copied the website URL
12. Opened the URL in Google Chrome
13. Successfully accessed the HTML webpage

## 📄 Website File

For the static website, I uploaded:

```text id="pj2r4n"
index.html
```

The `index.html` file acted as the main webpage of the static website.

## 🔐 Bucket Policy

To allow users to access the website objects publicly, I configured an appropriate **Bucket Policy**.

The policy allows the required read access to the website objects.

Conceptually:

```text id="6a2b6h"
Website Visitor
      ↓
S3 Website Endpoint
      ↓
S3 Bucket
      ↓
Bucket Policy
      ↓
Read Object
      ↓
index.html
```

### ⚠️ Security Learning

For a public S3 static website, the required public access configuration must be enabled appropriately, including adjusting **Block Public Access** settings when necessary and using a bucket policy that grants only the required access.

Public access should only be used when the website or objects are intentionally meant to be publicly accessible.

## 🌐 Website Testing

After enabling Static Website Hosting, S3 provided a website endpoint.

I copied the endpoint and opened it in my local Google Chrome browser.

```text id="4n3h8s"
S3 Website Endpoint
        ↓
     Chrome
        ↓
   index.html
        ↓
  Static Web Page
```

### ✅ Result

The HTML webpage hosted inside the S3 bucket was successfully displayed in the browser through the S3 static website endpoint.

## 💡 Key Learning

I learned:

* What Amazon S3 is
* Why it is called Simple Storage Service
* What an S3 bucket is
* Why S3 bucket names must be globally unique
* S3 global bucket naming concept
* S3 Regions
* Object storage
* Static website hosting
* `index.html`
* Bucket Policies
* Public object access
* S3 website endpoint

## 🔄 Complete Project Flow

```text id="h5b5x9"
Create S3 Bucket
       ↓
Upload index.html
       ↓
Enable Static Website Hosting
       ↓
Configure Required Public Access
       ↓
Configure Bucket Policy
       ↓
Get Website Endpoint
       ↓
Open URL in Chrome
       ↓
Static Website Successfully Displayed
```

## 🎯 Project Outcome

Successfully hosted a **static HTML website using Amazon S3** and accessed the webpage through the S3 website endpoint.

This hands-on project gave me practical experience with **S3 Buckets, Object Storage, Static Website Hosting, Bucket Policies and public access configuration**.
