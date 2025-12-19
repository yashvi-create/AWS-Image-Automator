📸 ImageAutomator: AWS Serverless Pipeline

🌟 Project Overview
This project demonstrates a fully automated **Serverless Architecture** built on AWS. It handles image uploads by processing them through a Lambda function and sending real-time email notifications to the administrator.

🏗️ Architecture
- Amazon S3: Acts as the entry point. Uploading an image to the `uploads` bucket triggers the workflow.
- AWS Lambda: A Python-based (Boto3) function that captures metadata, copies the file to a `processed` bucket, and triggers the notification service.
- Amazon SNS: Sends an instant email alert to confirm successful processing.
- IAM: Manages the "Least Privilege" security policies between services.

🛠️ Key Challenges & Solutions
- Timeout Fix: Increased Lambda timeout to 30s to ensure network tasks (S3 Copy/SNS Publish) complete successfully.
- Data Handling: Resolved `KeyError: 'Records'` by correctly parsing the S3 event structure in Python.
- Permission Mapping: Attached specific IAM policies for SNS and S3 to allow secure cross-service communication.

🚀 How to Use
1. Clone this repository.
2. Deploy the `lambda_function.py` to an AWS Lambda function.
3. Add an S3 trigger for "All object create events".
4. Replace the `TopicArn` in the code with your specific SNS Topic ARN.