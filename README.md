Serverless Automated Market Tracker

Objective
An event-driven, serverless data pipeline built in AWS that automatically fetches daily stock market closing data, stores it in a NoSQL database, and triggers an email notification to end-users.

Architecture & Services Used
Compute: AWS Lambda (Python 3.12, Boto3)

Database: Amazon DynamoDB

Automation/Cron: Amazon EventBridge

Messaging: Amazon SNS

Security: AWS IAM (Strict least-privilege execution roles)

How It Works
EventBridge triggers the Lambda function daily at 4:30 PM EST.

Lambda fetches real-time SPY closing prices and trading volume via public API.

The data is parsed and written as a new item in a DynamoDB table.

Upon a successful database write, Lambda publishes a message to an SNS topic, sending an email alert to subscribed users.

Key Learnings
Implementing IAM policies to securely allow Lambda to write to DynamoDB and publish to SNS without exposing overarching account access.

Utilizing the boto3 SDK to programmatically interact with AWS infrastructure.

Navigating the SNS Sandbox and configuring double opt-in email subscription protocols.
