# Task 4- Cloud Computing

**Name** : CODTECH IT SOLUTIONS

**Name** : Khushboo Vijay Patil

**Intern ID** : CT06DF672

**Domain** : Cloud Computing

**Duration** : 6 Weeks

**Mentor** : Neela Santosh

**Description of Task**

1. IAM Policies Setup
Step 1.1: Create IAM Groups and Assign Permissions
Go to IAM Console
Click on Groups → Create New Group
Attach Policies (AWS Managed or Custom)
AmazonS3ReadOnlyAccess (for read-only)
AmazonEC2FullAccess (for EC2 management)

Step 1.2: Create IAM Users
Go to IAM → Users → Add user
Username: dev_user1
Enable Programmatic access and/or Console access
Add user to a group (created above)

Step 1.3: Apply Fine-Grained Policies
Create custom IAM policies:
json
Copy
Edit
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "s3:DeleteObject",
      "Resource": "arn:aws:s3:::secure-bucket/*"
    }
  ]
}
Attach to specific users/groups/roles

2. Secure Storage Setup (Amazon S3)
Step 2.1: Create Secure Bucket
Go to S3 → Create Bucket
Region: select your preferred region
Uncheck Block all public access only if necessary

Step 2.2: Enable Bucket Versioning & Logging
Enable Versioning to recover overwritten/deleted files
Enable Access logging for tracking access
Target bucket: logs-bucket

Step 2.3: Set Bucket Policy for Restricted Access
json
Copy
Edit
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Deny",
    "Principal": "*",
    "Action": "s3:*",
    "Resource": [
      "arn:aws:s3:::task4-user",
      "arn:aws:s3:::task4-user/*"
    ],
    "Condition": {
      "Bool": {"aws:SecureTransport": "false"}
    }
  }]
}
Denies access if not using HTTPS

3. Data Encryption Setup
Step 3.1: Encryption At-Rest (S3)
Go to S3 → Bucket → Properties
Enable Default encryption
Choose AWS-KMS or SSE-S3

Step 3.2: Create a KMS Key (for custom control)
Go to KMS → Create Key
Select Symmetric Key
Define alias: secure-key
Set key administrators and usage permissions

Step 3.3: Attach KMS Key to S3
In S3 Bucket settings, choose your KMS key
Enables fine-grained control 

Step 3.4: Encryption In-Transit
Enforce HTTPS using:
IAM Policy
Bucket Policy (already done above)
For apps: Use HTTPS endpoints (https://task4-user.s3.ap-south-1.amazonaws.com/task+1.txt)

**OUTPUT**

![Image](https://github.com/user-attachments/assets/a14bbe09-3009-48b2-90fe-265fffd3f2a5)
![Image](https://github.com/user-attachments/assets/096de4e0-14a4-4660-9a3d-338ddb7a1518)
![Image](https://github.com/user-attachments/assets/ca5a9716-54d7-4da9-889b-bfe61106e44d)
![Image](https://github.com/user-attachments/assets/75ef701a-29f2-4acf-8faf-37e5e84a0d3a)
![Image](https://github.com/user-attachments/assets/6baa0310-a804-4150-a417-37187c6b268f)
![Image](https://github.com/user-attachments/assets/d0d9238f-23bb-497e-b9e6-f38f4e6b3ed2)
![Image](https://github.com/user-attachments/assets/53b6a7a7-e74b-49d1-a871-c3b212bb1d78)
