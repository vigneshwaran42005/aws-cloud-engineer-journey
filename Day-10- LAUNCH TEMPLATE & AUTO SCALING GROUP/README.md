# Day 10 – Launch Template & Auto Scaling Group 🚀

## 📅 Topic

**Launch Template & Auto Scaling Group**

## 📌 What I Learned

In this session, I learned how to create a **Launch Template** and use it with an **Auto Scaling Group (ASG)** to automatically manage EC2 instances based on workload.

I also practiced **dynamic scaling** by increasing CPU utilization on a Windows EC2 instance and observing the Auto Scaling Group launch an additional instance when the configured scaling condition was met.

## 🏗️ Architecture

```text id="5x6e7u"
                    Auto Scaling Group
                           │
                           ↓
                    Launch Template
                           │
             ┌─────────────┴─────────────┐
             │                           │
          EC2-1                       EC2-2
       Existing                  Automatically
                                  Launched
```

## 📋 Launch Template

A **Launch Template** contains the configuration required to launch EC2 instances.

I configured the Launch Template with settings such as:

* AMI
* Instance type
* Key pair
* Security Group
* Storage configuration
* Other EC2 launch settings

The Auto Scaling Group uses this Launch Template when creating new EC2 instances.

## 🔄 Auto Scaling Group

An **Auto Scaling Group** automatically manages the number of EC2 instances based on the configured capacity and scaling policies.

For my hands-on practice, I configured:

```text id="q2br5u"
Minimum Capacity: 1
Maximum Capacity: 3
```

This means the Auto Scaling Group maintains at least one instance and can increase the number of instances up to three based on the configured scaling conditions.

## 📈 CPU-Based Scaling Project

To test Auto Scaling, I created a Windows EC2 instance through the Launch Template and placed it under the Auto Scaling Group.

I then connected to the Windows EC2 instance using **RDP**.

Inside the Windows server, I used **PowerShell** to generate CPU load for testing purposes.

```text id="v9m1p2"
Windows EC2
     ↓
RDP Login
     ↓
PowerShell
     ↓
CPU Utilization Increased
     ↓
Auto Scaling Policy
     ↓
New EC2 Instance
```

## ⏱️ Scaling Condition

I configured the Auto Scaling Group to respond when the CPU utilization remained above the configured threshold for the specified evaluation period.

For example:

```text id="gq4q1b"
CPU Utilization
      ↓
Above Configured Threshold
      ↓
Condition Maintained
      ↓
Auto Scaling Group
      ↓
Launch New EC2 Instance
```

After increasing CPU utilization and waiting for the configured evaluation period, the Auto Scaling Group automatically launched another EC2 instance.

## 🧪 Scaling Test

Initially:

```text id="jz0q9u"
Auto Scaling Group

Desired Capacity: 1
Minimum Capacity: 1
Maximum Capacity: 3

Running:
EC2-1
```

After CPU utilization increased:

```text id="0x7gdy"
High CPU Utilization
        ↓
Scaling Condition Met
        ↓
Auto Scaling Group
        ↓
New Instance Launched
```

Result:

```text id="9e3c4v"
EC2-1  ← Existing Instance
EC2-2  ← Automatically Launched
```

This demonstrated **scale-out**, where the Auto Scaling Group increases capacity to handle increased workload.

## 🔽 Scale-In Concept

I also learned about **scale-in**, where the Auto Scaling Group reduces the number of instances when demand decreases.

```text id="y8s2v4"
Low Workload
    ↓
Scaling Condition
    ↓
Auto Scaling Group
    ↓
Instance Terminated
```

Scale-in helps reduce unnecessary infrastructure usage and cost.

## 🗑️ Auto Scaling Termination Policy

I also practiced how an Auto Scaling Group decides which instance to terminate during a scale-in event.

For example, the **OldestInstance** termination policy can be used when the intention is to terminate the oldest instance first.

```text id="0cbj49"
EC2-1 → Older Instance
EC2-2 → Newer Instance
        ↓
Scale-In
        ↓
OldestInstance Policy
        ↓
EC2-1 Terminated
```

### ⚠️ Important Difference

**Scale-In Protection** and **Termination Policy** are different concepts.

```text id="e9sl8p"
Scale-In Protection
→ Protects an instance from being terminated during scale-in.

Termination Policy
→ Helps determine which instance the ASG should terminate.
```

## 🧪 Hands-on Practice

During this project, I practiced:

1. Created a Launch Template
2. Configured AMI and instance type
3. Configured Key Pair
4. Configured Security Group
5. Created an Auto Scaling Group
6. Attached the Launch Template to the ASG
7. Configured VPC and subnets
8. Configured minimum capacity
9. Configured maximum capacity
10. Configured desired capacity
11. Configured CPU-based scaling
12. Connected to the Windows EC2 using RDP
13. Generated CPU load using PowerShell
14. Monitored CPU utilization
15. Waited for the configured scaling condition
16. Observed the Auto Scaling Group launch a new EC2 instance
17. Tested scale-out behavior
18. Learned the scale-in process
19. Practiced Auto Scaling termination policies

## 💡 Key Learning

This project helped me understand how **Launch Templates and Auto Scaling Groups** work together to provide automatic EC2 capacity management.

I also gained practical experience with:

* Launch Templates
* Auto Scaling Groups
* Minimum / Maximum / Desired Capacity
* Dynamic Scaling
* CPU-based Scaling
* Scale-Out
* Scale-In
* CloudWatch Metrics
* Windows EC2
* RDP
* PowerShell
* Auto Scaling Termination Policies

## 🔄 Complete Scaling Flow

```text id="l5m0zk"
Launch Template
       ↓
Auto Scaling Group
       ↓
EC2 Instance
       ↓
CPU Load Generated
       ↓
CPU Utilization Increases
       ↓
Scaling Condition Met
       ↓
Scale-Out
       ↓
New EC2 Instance Launched
```

## 🎯 Project Outcome

Successfully created a **Launch Template and Auto Scaling Group**, configured capacity limits and CPU-based scaling, and tested automatic EC2 instance creation by generating CPU load on a Windows EC2 instance.

This hands-on project helped me understand how AWS can automatically increase or decrease compute capacity based on application workload.
