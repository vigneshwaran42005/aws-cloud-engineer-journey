Day 16 – SNS, SQS & Resume Notification Automation 📩🔄
📅 Topic

Amazon SNS, Amazon SQS & Serverless Email Notification Automation

📌 What I Learned

In this session, I learned about Amazon SNS (Simple Notification Service) and Amazon SQS (Simple Queue Service).

I also built a serverless resume-processing and notification workflow using:

Amazon S3
AWS Lambda
Amazon SNS
Amazon SQS
Amazon DynamoDB
Amazon SES
Lambda Layers
Python
📢 Amazon SNS

Amazon SNS (Simple Notification Service) is a managed publish/subscribe messaging service.

SNS can send a published message to multiple subscribers such as:

Email
Lambda
SQS
HTTP/HTTPS endpoints
Other supported AWS integrations

Simple concept:

Publisher
    ↓
SNS Topic
    ↓
Subscribers

SNS is useful when the same event needs to notify multiple consumers.

📬 Amazon SQS

Amazon SQS (Simple Queue Service) is a managed message queuing service.

Messages are placed into a queue and remain available for consumers to process according to the queue's retention and processing configuration.

Simple concept:

Producer
   ↓
SQS Queue
   ↓
Consumer

The consumer can process the message when it is ready.

🔄 SNS vs SQS
SNS	SQS
Publish/Subscribe	Message Queue
Push-based messaging	Queue-based messaging
Sends messages to subscribers	Stores messages until consumed/retention expires
One message can fan out to multiple subscribers	Consumer processes messages from the queue
Useful for notifications and event distribution	Useful for decoupling applications and asynchronous processing
💡 Easy Way to Remember

SNS = Notify / Fan-out
SQS = Queue / Wait for Processing

🧪 Project 1 – S3 → SNS → SQS

For the first hands-on project, I created a workflow where uploading a resume to an S3 bucket generated a notification through SNS and the message could be delivered to an SQS queue.

🏗️ Architecture
User
 │
 │ Upload Resume
 ↓
S3 Bucket
 │
 │ Event
 ↓
SNS Topic
 │
 ↓
SQS Queue
 │
 ↓
Message Available for Processing
🪣 S3 Bucket

I created an S3 bucket with a resume location/folder for uploaded files.

S3 Bucket
    │
    └── resume/
          ├── candidate1.pdf
          ├── candidate2.pdf
          └── candidate3.pdf
📢 SNS Topic

I created an SNS Topic and configured the required integration.

When a resume upload event occurred, the notification could be published to the SNS topic.

S3 Event
   ↓
SNS Topic
   ↓
Notification
📬 SQS Queue

I created an SQS Queue and connected it as a subscriber to SNS.

SNS Topic
    ↓
SQS Queue
    ↓
Message

I verified that the notification message was available inside the SQS queue.



