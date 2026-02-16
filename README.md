# Event-Driven-Architecture-AWS
This project demonstrates an event-driven architecture using AWS services to build a real-time data processing pipeline. The architecture is designed to process events generated in an S3 bucket and uses services like SNS, SQS, and Lambda for reliable, scalable event processing.

Project Overview

This project demonstrates an event-driven architecture built on Amazon Web Services (AWS) to create a real-time, scalable, and reliable data processing pipeline.

The system processes events generated in an Amazon S3 bucket and uses AWS services such as:

Amazon Web Services

Amazon S3

Amazon SNS

Amazon SQS

AWS Lambda

<img width="728" height="231" alt="image" src="https://github.com/user-attachments/assets/7dc10de6-4a52-4a17-91cb-6ac0923c3253" />


The architecture ensures loose coupling between components, fault tolerance, scalability, and reliable event delivery.

Architecture Components
1️⃣ Event Producer – Source S3 Bucket

The Source S3 Bucket acts as the event producer.
Whenever an object is:

Created

Modified

Deleted

An event notification is generated automatically.

2️⃣ Event Ingestion – SNS Topic

The event from S3 is sent to an SNS topic.

SNS acts as:

The event ingestion layer

A pub/sub messaging system

A distributor of messages to subscribers

It forwards the event to one or more subscribed services.

3️⃣ Event Stream – SQS Queue

SQS subscribes to the SNS topic and receives the event.

SQS provides:

Reliable message buffering

Decoupling between producer and consumer

Retry mechanism

Ordered processing (if FIFO queue is used)

This ensures no event is lost even if downstream processing is delayed.

4️⃣ Event Consumer – Lambda Function

The Lambda function is triggered by messages in SQS.

Lambda performs:

Data validation

Transformation

Business logic execution

File processing

This serverless approach ensures automatic scaling and cost efficiency.

5️⃣ Event Sink – Target S3 Bucket

After processing, the Lambda function writes the transformed or processed data into the Target S3 Bucket, completing the pipeline.

Complete Workflow

A file is uploaded to the Source S3 Bucket.

S3 generates an event notification.

The event is sent to the SNS Topic.

SNS distributes the event to the SQS Queue.

SQS buffers the event and triggers the Lambda function.

Lambda processes the data.

The processed output is stored in the Target S3 Bucket.
