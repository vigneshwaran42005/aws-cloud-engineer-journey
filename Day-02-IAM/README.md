# Day 02 – AWS IAM 🔐

## 📅 Topic

**AWS Identity and Access Management (IAM)**

## 📌 What I Learned

AWS Identity and Access Management (IAM) is an AWS service used to securely control access to AWS resources.

IAM helps us manage:

* Who can access AWS resources
* What actions users or services can perform
* Which AWS resources they can access
* How permissions are granted and controlled

## 🔑 Key IAM Components

### 1. Root User

The Root User is the account owner created when an AWS account is first created.

The Root User has complete access to the AWS account.

**Best Practice:** Avoid using the Root User for everyday AWS tasks.

### 2. IAM User

An IAM User represents a person or application that needs access to AWS resources.

Example:

```text
Developer → IAM User → AWS Resources
```

### 3. IAM Group

An IAM Group is a collection of IAM users.

Instead of assigning permissions to each user individually, permissions can be attached to a group.

Example:

```text
Developers Group
       │
 ┌─────┼─────┐
 │     │     │
User1 User2 User3
```

### 4. IAM Policy

An IAM Policy is a JSON document that defines permissions.

It determines **what actions can be performed on which AWS resources**.

Example:

```text
Allow → S3 Read
Allow → S3 Write
Deny  → S3 Delete
```

### 5. IAM Role

An IAM Role provides temporary permissions that can be assumed by trusted entities such as AWS services, IAM users or applications.

A Role mainly involves two important policies:

#### 🔐 Permission Policy – "What can access?"

The **Permission Policy** defines **what actions the trusted entity is allowed or denied to perform**.

Example:

```text
EC2
 ↓
Permission Policy
 ↓
Allow: s3:GetObject
Allow: s3:PutObject
```

This answers:

> **"What can this role do?"**

#### 🤝 Trust Policy – "Who can access?"

The **Trust Policy** defines **who or what is allowed to assume the IAM Role**.

Example:

```text
EC2
 ↓
Trust Policy
 ↓
Allowed to Assume Role
```

This answers:

> **"Who can assume this role?"**

### 💡 Easy Way to Remember

> **Permission Policy = WHAT can you do?**
> **Trust Policy = WHO can use/assume the role?**

Example:

```text
              IAM ROLE
                 │
        ┌────────┴────────┐
        │                 │
 Permission Policy    Trust Policy
        │                 │
     WHAT?              WHO?
        │                 │
  S3 Read/Write          EC2
```

### 🧠 Real-World Example

Think about an office employee:

**Trust Policy:**

> "This employee is allowed to enter this department."

**Permission Policy:**

> "Once inside, this employee can read files but cannot delete them."

So:

**Trust = Who can enter/use the role**
**Permission = What they can do after getting access**

## 🛡️ IAM Best Practices

* Avoid using the Root User for daily activities
* Give users only the permissions they require
* Use IAM Roles instead of hard-coded credentials where possible
* Use groups to manage permissions for multiple users

## 🧪 Hands-on Practice

During this session, I practiced the basic IAM workflow:

1. Explored the IAM Dashboard
2. Created an IAM User
3. Created an IAM Group
4. Attached permissions using IAM Policies
5. Created and explored IAM Roles
6. Understood Permission Policies
7. Understood Trust Policies
8. Reviewed user and role permissions



## 💡 Key Learning

I learned how AWS IAM provides centralized identity and access control for AWS resources.

I understood the difference between **IAM Users, Groups, Policies and Roles**.

Most importantly, I learned:

> **Permission Policy → What can the role do?**
> **Trust Policy → Who can assume the role?**

I also understood why the **principle of least privilege** is important for AWS security.

## 🎯 AWS Focus

The main focus of this session was understanding how to securely manage identities, authentication, authorization and role-based access in AWS using IAM.
