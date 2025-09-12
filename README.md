# AWS
# Coud-Computing-AWS
```
✅ 1. What is AWS?
AWS (Amazon Web Services) is a cloud platform that offers a wide range of services like compute power, storage, databases, networking, security, analytics, and more.
It helps companies scale their infrastructure without owning physical servers.

✅ 2. Key AWS Concepts
Concept	Description
Cloud Computing	On-demand delivery of IT resources over the internet.
IaaS	Infrastructure as a Service (EC2, S3, VPC).
PaaS	Platform as a Service (Elastic Beanstalk, RDS).
SaaS	Software as a Service (Gmail, Office 365).

✅ 3. AWS Global Infrastructure
Regions → Geographical locations (ex: us-east-1, ap-south-1).
Availability Zones (AZ) → Isolated data centers in a Region.
Edge Locations → Used by CloudFront (CDN).

✅ 4. Core AWS Services
1️⃣ Compute Services
➔ EC2 (Elastic Compute Cloud)
Launch virtual servers (instances).
Example:
Launch EC2 instance (Amazon Linux).
SSH Access Example:
ssh -i mykey.pem ec2-user@ec2-public-ip
➔ Lambda (Serverless Compute)
Run code without managing servers.
Example: Simple Python Lambda function
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello from AWS Lambda!'
    }

2️⃣ Storage Services
➔ S3 (Simple Storage Service)
Object storage for files.
Example: Upload file using AWS CLI
aws s3 cp sample.txt s3://my-bucket-name/sample.txt
➔ EBS (Elastic Block Store)
Persistent block-level storage attached to EC2.

3️⃣ Database Services
➔ RDS (Relational Database Service)
Managed SQL databases (MySQL, PostgreSQL).
Example: Connect to RDS
mysql -h your-rds-endpoint.amazonaws.com -u admin -p
➔ DynamoDB
NoSQL database.

4️⃣ Networking Services
➔ VPC (Virtual Private Cloud)
Isolated network.
Example Components of VPC
Subnets
Route Tables
Internet Gateway (IGW)
Security Groups
➔ CloudFront
Content Delivery Network (CDN).
Use Case Example: Distribute static website assets globally with low latency.

✅ 5. Security in AWS
➔ IAM (Identity and Access Management)
Create Users, Roles, Policies.
Example: Create IAM User CLI
aws iam create-user --user-name AnilUser
Example: Attach Policy
aws iam attach-user-policy --user-name AnilUser --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess

✅ 6. Monitoring & Logging
➔ CloudWatch
Monitor metrics (CPU usage, memory).
Example: Create CloudWatch Alarm

aws cloudwatch put-metric-alarm \
    --alarm-name HighCPUUtilization \
    --metric-name CPUUtilization \
    --namespace AWS/EC2 \
    --statistic Average \
    --period 300 \
    --threshold 80 \
    --comparison-operator GreaterThanThreshold \
    --evaluation-periods 2 \
    --alarm-actions arn:aws:sns:region:account-id:my-sns-topic

➔ CloudTrail
Track API activity and changes.

✅ 7. Deployment & Automation
➔ CloudFormation
Infrastructure as Code (IaC).
Example: Simple CloudFormation YAML Template

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0abcdef1234567890

➔ CodePipeline
CI/CD Automation.

✅ 8. Hands-on Example: Deploy Simple Website on S3 + CloudFront
Step 1: Create S3 Bucket
aws s3 mb s3://my-website-bucket

Step 2: Enable Static Website Hosting
aws s3 website s3://my-website-bucket --index-document index.html

Step 3: Upload Files
aws s3 cp index.html s3://my-website-bucket/index.html

Step 4: Configure CloudFront

Create distribution via AWS Console.

Use S3 bucket as origin.

✅ 9. Basic Pricing Concept
EC2: Pay per second.
S3: Pay per GB stored.
Lambda: Pay per request and compute time.
Free Tier Available: Useful for beginners.

✅ 10. Best Practices
Use IAM Roles instead of hardcoding keys.
Enable versioning in S3 for backup.
Set up multi-AZ for RDS for High Availability.
Use security groups to allow only required ports.

✅ 11. Useful AWS CLI Commands
Command	Description
aws s3 ls	List S3 buckets
aws ec2 describe-instances	List EC2 instances
aws iam list-users	List IAM users
aws lambda list-functions	List Lambda functions

✅ 12. Summary
Component	Example
Compute	EC2 Instance, Lambda function
Storage	S3 Bucket
Database	RDS MySQL instance
Networking	VPC with Subnets & IGW
Security	IAM Policies & Roles
Monitoring	CloudWatch Alarm
IaC	CloudFormation template
CDN	CloudFront Distribution

✅ 13. Key AWS Concepts to Remember
Regions and AZs
EC2 vs Lambda vs ECS
S3 vs EBS vs EFS
RDS vs DynamoDB
```
---
---
# AWS
# 🚀 AWS Cloud Engineer
AWS Cloud Engineer roles. It is organized into key sections covering Compute, Storage, Networking, IAM, Cloud Migration, IaC, Cost Optimization, OS Basics, Database Services, and DevOps.

---

## ✅ Section 1 – AWS Compute Services

### Q1. What is EC2 in AWS?  
EC2 (Elastic Compute Cloud) provides scalable virtual servers in the cloud.  
👉 Example: Launch an EC2 instance to host a simple website.

---

### Q2. What are the types of EC2 pricing models?  
- On-Demand: Pay per use.  
- Reserved: Pre-pay for 1–3 years → Cheaper.  
- Spot Instances: Cheap but can be terminated anytime.

---

### Q3. What is an AMI (Amazon Machine Image)?  
A template with OS and pre-installed software to launch EC2 instances.

---

### Q4. What is Auto Scaling?  
Automatically adjusts the number of EC2 instances based on load.  
👉 Example: Auto Scaling increases instances when traffic spikes.

---

### Q5. What is Elastic Load Balancer (ELB)?  
Distributes incoming traffic across multiple EC2 instances.

---

### Q6. How do you connect to an EC2 instance?  
Using SSH (Linux) or RDP (Windows).  
👉 Example: ssh -i mykey.pem ec2-user@public-ip

---

### Q7. What is the difference between Public and Private EC2 Instances?  
- Public: Accessible from Internet.  
- Private: Internal network only.

---

### Q8. What is User Data in EC2?  
Scripts that run at instance launch to configure the server.  
👉 Example: Auto-install Apache on boot.

---

### Q9. What happens if EC2 stops and starts again?  
Public IP changes unless Elastic IP is used. EBS data remains.

---

### Q10. Why use Elastic IP?  
Elastic IP is static and remains same after stop/start operations.

---

## ✅ Section 2 – AWS Storage Services

### Q1. What is S3 in AWS?  
Object storage service to store files (images, documents).

---

### Q2. What are S3 Storage Classes?  
- Standard,  
- Infrequent Access (IA),  
- Glacier (Archive).

---

### Q3. What is Versioning in S3?  
Keeps multiple object versions to recover from accidental deletes.

---

### Q4. What is EBS?  
Block-level storage for EC2 (like virtual hard disk).

---

### Q5. Difference between S3 and EBS?  
- S3 → Object storage, scalable.  
- EBS → Block storage, attached to EC2.

---

### Q6. What happens to EBS data on instance termination?  
Depends on "Delete on Termination" flag.

---

### Q7. What is Storage Gateway?  
Connects on-premises apps to AWS Cloud Storage.

---

### Q8. How to restrict public access to S3 bucket?  
Use Bucket Policies or Block Public Access settings.

---

### Q9. What is Multipart Upload?  
Upload large objects in parts to improve reliability.

---

### Q10. Example use case of S3 and EBS?  
Store user images in S3, use EBS for EC2 OS disk.

---

## ✅ Section 3 – Networking in AWS

### Q1. What is a VPC?  
Virtual Private Cloud where you launch AWS resources.

---

### Q2. What are Subnets?  
Segments of VPC:  
- Public → Internet accessible.  
- Private → Internal only.

---

### Q3. What is an Internet Gateway?  
Allows VPC resources to connect to the Internet.

---

### Q4. What is NAT Gateway?  
Allows private instances to access Internet without being publicly exposed.

---

### Q5. What is Route53?  
Managed DNS service mapping domain names to IPs.

---

### Q6. What is VPC Peering?  
Private connection between two VPCs.

---

### Q7. What is Direct Connect?  
Dedicated private network connection to AWS.

---

### Q8. Difference between Public and Private IP?  
Public IP → Internet accessible.  
Private IP → Internal only.

---

### Q9. Example of Security Group use?  
Allow SSH (port 22) only from specific IP address.

---

### Q10. What is CloudFront?  
CDN to deliver content globally at low latency.

---

## ✅ Section 4 – IAM (Identity & Access Management)

### Q1. What is IAM?  
Controls user access to AWS services.

---

### Q2. IAM User vs IAM Role?  
- User → Permanent credentials.  
- Role → Temporary permissions for resources.

---

### Q3. What is an IAM Policy?  
JSON document defining allowed or denied actions.

---

### Q4. What is MFA?  
Multi-Factor Authentication for extra security.

---

### Q5. What is Federation in IAM?  
Login using existing AD credentials (SAML).

---

### Q6. Example use case for IAM Role?  
Grant EC2 permission to read from S3.

---

### Q7. What is Least Privilege Principle?  
Grant minimum necessary permissions.

---

### Q8. How to secure S3 Bucket access?  
Bucket Policy + IAM Policy + Block Public Access.

---

### Q9. Can IAM users share credentials?  
No, each user has individual credentials.

---

### Q10. Group vs Role?  
Group → Multiple users.  
Role → Assigned to AWS resources.

---

## ✅ Section 5 – Cloud Migration

### Q1. What is Cloud Migration?  
Moving apps/data from on-prem to AWS Cloud.

---

### Q2. Steps in Cloud Migration?  
1. Assessment → 2. Planning → 3. Execution → 4. Validation → 5. Go-live

---

### Q3. AWS Migration Tools?  
Migration Hub, Application Migration Service.

---

### Q4. Common Challenges?  
Bandwidth limits, downtime, compatibility.

---

### Q5. How to reduce downtime?  
Use replication and schedule during off-hours.

---

### Q6. What is Rehosting?  
“Lift and Shift” without code changes.

---

### Q7. What is Re-platforming?  
Partial code changes to use cloud features.

---

### Q8. Why assessment before migration?  
To estimate cost & ensure compatibility.

---

### Q9. AWS Migration Hub usage?  
Track progress of migrations.

---

### Q10. Example Scenario?  
Migrated web app to EC2 + S3 using Application Migration Service.

---

## ✅ Section 6 – Infrastructure as Code (IaC)

### Q1. What is IaC?  
Manage cloud infrastructure via code.

---

### Q2. What is CloudFormation?  
AWS-native IaC service using YAML/JSON.

---

### Q3. What is Terraform?  
Third-party tool, works across clouds.

---

### Q4. Terraform Workflow Commands?  
- terraform init  
- terraform plan  
- terraform apply  
- terraform destroy

---

### Q5. Why use IaC?  
Version control + repeatable deployments.

---

### Q6. Example Terraform file function?  
Launch EC2 instance.

---

### Q7. Mutable vs Immutable Infrastructure?  
Mutable → Modify existing.  
Immutable → Recreate new.

---

### Q8. Can you write CloudFormation manually?  
Yes, YAML defining EC2, SG, etc.

---

### Q9. Example CloudFormation use?  
Deploy EC2 automatically.

---

### Q10. Why state management in Terraform?  
Track existing infra vs desired state.

---

## ✅ Section 7 – Cost Optimization

### Q1. AWS Pricing Model?  
On-Demand, Reserved, Spot.

---

### Q2. Reduce EC2 cost?  
Use Reserved or Spot Instances.

---

### Q3. AWS Free Tier?  
Free usage up to limits for 1 year.

---

### Q4. S3 cost reduction?  
Archive old data to Glacier.

---

### Q5. What is AWS Cost Explorer?  
Analyze and visualize spending.

---

### Q6. When to use Spot Instances?  
For batch jobs where interruptions are okay.

---

### Q7. How to monitor costs?  
AWS Budgets + Cost Explorer.

---

### Q8. AWS Trusted Advisor?  
Recommends cost/security/performance improvements.

---

### Q9. What is Reserved Instance?  
Prepaid long-term cheaper EC2 instance.

---

### Q10. Example cost optimization strategy?  
Auto shutdown non-prod EC2 at night.

---

## ✅ Section 8 – OS Basics (Windows/Linux)

### Q1. Check disk usage in Linux?  
df -h

---

### Q2. List running processes?  
ps -aux or top

---

### Q3. Connect to EC2 via SSH?  
ssh -i key.pem ec2-user@public-ip

---

### Q4. What is IIS?  
Web server for Windows.

---

### Q5. Example Linux directories?  
/etc → Config files, /var → Logs, /home → Users.

---

### Q6. What is Active Directory?  
Central identity management (Windows).

---

### Q7. Check network config?  
ifconfig or ip a

---

### Q8. Change file permissions?  
chmod 755 filename

---

### Q9. FTP vs SFTP?  
SFTP → Secure (uses SSH), FTP → Insecure.

---

### Q10. Reboot Linux instance?  
sudo reboot

---

## ✅ Section 9 – Database Services

### Q1. What is AWS RDS?  
Managed relational DB service (MySQL, Aurora).

---

### Q2. What is DynamoDB?  
NoSQL key-value DB service.

---

### Q3. RDS vs DynamoDB?  
RDS → SQL DB, Dynamo → NoSQL.

---

### Q4. What is Multi-AZ?  
Automatic DB replication for availability.

---

### Q5. How to back up RDS DB?  
Automated/manual snapshots.

---

### Q6. What is Aurora?  
High-performance managed relational DB.

---

### Q7. What is Read Replica?  
Scale read queries via replication.

---

### Q8. Example DynamoDB use-case?  
Store user session data.

---

### Q9. RDS vs EC2-hosted DB?  
RDS → Managed backups and scaling.  
EC2 → Manual management.

---

### Q10. What is Provisioned Throughput (DynamoDB)?  
Pre-defined read/write capacity units.

---

## ✅ Section 10 – DevOps & CI-CD

### Q1. What is CI-CD?  
CI → Continuous Integration (automated code tests).  
CD → Continuous Delivery (automated deploy).

---

### Q2. What is CodePipeline?  
Service to automate build → test → deploy.

---

### Q3. What is CodeBuild?  
Fully managed build service.

---

### Q4. What is CodeDeploy?  
Automates code deployment to EC2 or on-prem.

---

### Q5. Why CI-CD is useful?  
Faster releases + fewer manual errors.

---

### Q6. What is Infrastructure Testing?  
Automated tests for IaC deployments.

---

### Q7. What is Blue/Green Deployment?  
Switch between two identical environments.

---

### Q8. What is Canary Deployment?  
Deploy to small subset of users first.

---

### Q9. Example automate EC2 provisioning?  
Use CloudFormation or Terraform templates.

---

### Q10. What is Monitoring in CI-CD?  
Use CloudWatch to track build & deploy logs.

---
---
