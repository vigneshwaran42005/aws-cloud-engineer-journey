# Day 12 – S3 Replication 🔄🪣

## 📅 Topic

**Amazon S3 Replication**

## 📌 What I Learned

In this session, I learned about **Amazon S3 Replication**, which is used to automatically replicate objects from one S3 bucket to another S3 bucket.

S3 Replication can help organizations maintain copies of data in another bucket for purposes such as **disaster recovery, data protection and business continuity**.

## 🪣 Source and Destination Buckets

For this hands-on practice, I created two S3 buckets:

```text id="0v8k3f"
Source S3 Bucket
       │
       │ Replication
       ↓
Destination S3 Bucket
```

The first bucket was configured as the **Source Bucket**, and the second bucket was configured as the **Destination Bucket**.

## 🔄 Replication Flow

```text id="o7x7e4"
Source Bucket
      │
      │ S3 Replication Rule
      ↓
Destination Bucket
      │
      ↓
Replicated Object
```

When an object is uploaded to the Source Bucket, the configured replication rule can replicate the object to the Destination Bucket.

## 🔐 IAM Role for Replication

I learned that S3 needs appropriate permissions to perform replication.

An **IAM Role** is configured so that Amazon S3 can access the required source and destination resources for the replication process.

```text id="s7w2t1"
Amazon S3
    │
    ↓
IAM Replication Role
    │
    ├── Read Source Object
    │
    └── Replicate to Destination
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created a Source S3 Bucket
2. Created a Destination S3 Bucket
3. Configured the required bucket settings
4. Enabled the required versioning configuration
5. Configured an S3 Replication Rule
6. Configured the required IAM Role
7. Selected the Destination Bucket
8. Configured replication permissions
9. Uploaded objects to the Source Bucket
10. Checked the Destination Bucket
11. Verified that the objects were replicated

## 💡 Key Learning

I learned how S3 Replication can automatically copy objects from a Source Bucket to a Destination Bucket.

The basic concept is:

```text id="g2kqz1"
Source Bucket
      ↓
Replication Rule
      ↓
IAM Permissions
      ↓
Destination Bucket
```

## 🎯 Project Outcome

Successfully configured an **S3 Replication setup** using a Source Bucket and Destination Bucket and learned how replication rules and IAM permissions work together.
