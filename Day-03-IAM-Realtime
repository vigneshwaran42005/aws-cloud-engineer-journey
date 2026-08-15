# Day 03 – IAM Hands-on & IAM Roles 🔐

## 📅 Topic

**IAM Hands-on – Users, Roles, Policies & Temporary Credentials**

## 📌 What I Learned

In this session, I moved from IAM theory to practical implementation.

I practiced how IAM Users and IAM Roles work together and how temporary credentials can be obtained by assuming an IAM Role.

## 🔄 IAM Role Concept

An IAM Role does not belong permanently to a specific user.

Instead, a trusted entity can **assume the role** and receive temporary security credentials.

```text
IAM User
   │
   │ Assume Role
   ↓
IAM Role
   │
   ↓
Temporary Credentials
   │
   ↓
AWS Resources
```

## 🔐 Trust Policy vs Permission Policy

### Trust Policy – WHO?

The Trust Policy defines **who or what is allowed to assume the role**.

```text
WHO can assume the role?
        ↓
   Trust Policy
```

### Permission Policy – WHAT?

The Permission Policy defines **what actions the role is allowed to perform** on AWS resources.

```text
WHAT can the role do?
        ↓
 Permission Policy
```

### Easy Way to Remember

> **Trust Policy = WHO can access/assume the role?**
> **Permission Policy = WHAT can they do?**

## 🧪 Hands-on Practice

During this session, I practiced:

1. Creating an IAM User
2. Creating an IAM Role
3. Configuring a Trust Policy
4. Attaching a Permission Policy
5. Allowing the required principal to assume the role
6. Using AWS CLI for IAM operations
7. Assuming an IAM Role
8. Working with temporary security credentials
9. Verifying the active identity using AWS STS

## 💻 AWS CLI Practice

After assuming the role, I used:

```bash
aws sts get-caller-identity
```

This command helps verify the AWS identity currently being used by the CLI.

It returns information such as:

* Account
* User ID
* ARN

## 🔑 Temporary Credentials

When an IAM Role is assumed, AWS provides temporary security credentials instead of requiring permanent access keys for the role.

```text
Access Key ID
Secret Access Key
Session Token
```

These temporary credentials can then be used to make authorized AWS API calls according to the role's permissions.

## 🛡️ Security Concept

Using IAM Roles and temporary credentials is generally preferred over storing long-term access keys in applications or servers.

This supports better security and follows the **Principle of Least Privilege**.

## 💡 Key Learning

I learned how to practically configure IAM Roles, Trust Policies and Permission Policies.

I also learned how to assume an IAM Role, obtain temporary credentials and verify the current AWS identity using AWS STS.

### Most Important Takeaway

```text
Trust Policy
     ↓
WHO can assume?

Permission Policy
     ↓
WHAT can they do?
```

## 🎯 AWS Focus

The main focus of Day 03 was gaining practical experience with **IAM Roles, Trust Policies, Permission Policies, AWS STS and temporary credentials**.
