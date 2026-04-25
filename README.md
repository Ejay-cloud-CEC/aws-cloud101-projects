  # AWS Cloud 101 Projects
My hands-on labs from AWS Educate at Cebu Eastern College 🚀

Module 4: AWS Core Services

# S3 Static Website Hosting
# April 20, 2026  
### AWS Educate Cloud 101 - Module 4 

Skills: Amazon S3, Cloud Architecture, GitHub, Technical Documentation

What I built:
- Designed S3 bucket architecture for static website hosting
- Configured bucket policy for public read access  
- Set up static website endpoint with index.html
- Documented cloud architecture for portfolio

**Architecture Diagram:**  
[📄 View S3 Static Website Architecture PDF](S3%20Static%20Website%20Hosting%20Architecture%20.pdf)

Key Learnings:
- S3 buckets can host static websites without EC2 servers
- Public access requires explicit bucket policy configuration
- Architecture diagrams communicate cloud solutions effectively
---
---
# AWS EC2 Concepts 
# April 21, 2026
### AWS Educate Cloud 101 - Module 4 

- Created EC2 architecture diagram showing SSH connection flow
- Documented 4-step process: Launch → Security Group → Key Pair → SSH
- Understood EC2 as virtual server with EBS storage
- Learned Security Group as firewall controlling Port 22 access

**Architecture Diagram:**
![EC2 Architecture](EC2%20Architecture.pdf)

Key Learnings:
- EC2 is AWS virtual server in the cloud
- Security Groups act as virtual firewall for EC2
- Key Pair (.pem file) enables secure SSH access
- EBS provides persistent block storage for EC2
---
---
# IT: Linux Basics - chmod 
# April 21,2026

**Commands Practiced:**
- `touch practice-key.pem` → Created dummy key file
- `chmod 400 practice-key.pem` → Set to read-only permission
- Result: `-r--------` = 400, AWS SSH requirement

**Key Learning:** AWS blocks SSH if .pem file is not 400 permission for security.

**Files:**
- [Linux Basics PDF](./Linux%20basics.pdf)
  ---
  --- 
# AWS VPC Architecture 
### April 22,2026
### AWS Educate Cloud 101 - Module 4 

### Diagram Preview
[View VPC Architecture PDF](./AWS%20VPC%20Architecture%20.pdf)

### Key Components
1. **User** - Client accessing AWS resources
2. **Internet Gateway** - Door to internet for VPC
3. **VPC 10.0.0.0/16** - Private cloud network with 65,536 IPs
4. **Public Subnet 10.0.1.0/24** - Subnet with internet access

### Launch Steps Summary
1. Create VPC with IPv4 CIDR 10.0.0.0/16 - Tenancy: Default
2. Create Subnets: Public 10.0.1.0/24 + Private 10.0.2.0/24
3. Create & Attach Internet Gateway to VPC
4. Configure Route Tables: 0.0.0.0/0 → Internet Gateway
5. Configure Security Groups: Allow Port 80, 22
6. Launch EC2 in Public Subnet with Auto-assign Public IP
7. Delete VPC + IGW after testing to avoid charges

### Key Learnings
- **VPC** = Your private cloud network. Isolated from other AWS customers
- **CIDR** = /16 gives 65,536 IPs. /24 gives 256 IPs per subnet
- **Internet Gateway** = Required for Public Subnet to access internet
- **Route Table** = Controls traffic flow. GPS sa network
- **Cost Control** = VPC is free but IGW + NAT Gateway have charges if left running
---
---
# AWS RDS MySQL Architecture 
### April 23, 2026
### AWS Educate Cloud 101 - Module 4 

**Architecture diagram for Amazon RDS MySQL deployment.**  
**Planning only. No resources launched to avoid AWS charges.**

### Diagram Preview
[View RDS Architecture PDF](./AWS%20RDS%20MySQL%20Architecture%20.pdf)

### Key Components
1. **User/Termux** - Client connecting to database
2. **Security Group** - Firewall allowing Port 3306
3. **RDS Instance** - Managed database service
4. **MySQL Database** - cloud101db

### Launch Steps Summary
1. Create RDS MySQL 8.0.35 - Free Tier db.t3.micro
2. Configure: cloud101db, admin, Cloud101!
3. Security: Public access Yes, Port 3306 open
4. Connect: `mysql -h <endpoint> -u admin -p`
5. Delete after testing to avoid charges

### Key Learnings
- **RDS** = Managed service. AWS handles backup, patching, scaling
- **Security Group** = Virtual firewall. Must open Port 3306 for remote access
- **Cost Control** = Always delete resources after demo

---
---
# SQLBolt 1-18 Complete ✅

Completed all 18 lessons of SQLBolt interactive SQL tutorial. 
From basic SELECT statements to CREATE TABLE and database design.

**Date Finished:** April 23, 2026  
**Time Spent:** 1 day intensive study  
**Status:** 100% Complete  

---

### 🧠 Key Skills Learned

**Querying:** `SELECT`, `WHERE`, `AND/OR`, `LIKE`, `ORDER BY`, `LIMIT`  
**Joins:** `INNER JOIN`, `LEFT JOIN`, `NULL` handling  
**Aggregates:** `COUNT()`, `SUM()`, `AVG()`, `GROUP BY`, `HAVING`  
**CRUD:** `INSERT INTO`, `UPDATE`, `DELETE FROM`  
**DDL:** `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`  

---

### 📸 Proof of Completion

[View SQLBolt Completion Certificate](./SQLBolt-complete.png.pdf)

*Note: Click link to view PDF proof*

---

### ☁️ AWS Relevance

SQL skills for: Amazon RDS, Amazon Athena, Redshift, CloudWatch Logs Insights
---
---
# 🔐 AWS IAM Architecture 
# Cloud 101 Module 4
> **Identity and Access Management** |
# APRIL 24 2026
[[AWS](https://img.shields.io/badge/AWS-IAM-FF9900?style=for-the-badge&logo=amazon-aws)](https://aws.amazon.com/iam/)
[[Security](https://img.shields.io/badge/Model-Zero%20Trust-DC143C?style=for-the-badge)](./IAM%20ARCHITECTURE%20.pdf)
[[Status](https://img.shields.io/badge/Lab-Complete-00C851?style=for-the-badge)](#)

[📄 View Architecture Diagram PDF](./IAM%20ARCHITECTURE%20.pdf)
---

### 🧩 **Components Breakdown**

| Component | Name Used | Purpose | Best Practice | Boss Analogy |
| --- | --- | --- | --- | --- |
| **Root User** | Account Owner | Unlimited access | Billing only + MFA | Tag-iya sa kompanya |
| **IAM User** | `ejay-dev` | Human identity | 1 person = 1 user | Employee ID badge |
| **IAM Group** | `Developers` | Team permissions | Attach policy to group | Department |
| **IAM Role** | `EC2-S3-Role` | Temp AWS service creds | Use for EC2/Lambda | Visitor badge |
| **Policy** | `GetCloud101Objects` | JSON allow/deny rules | Least privilege only | List sa pwede sudlan |
| **MFA** | Authenticator App | Second factor auth | Required for admins | Double lock |

---

### 🛠️ **6 Steps to Build**

1. **Create IAM User** → `ejay-dev` with Console + Programmatic access + Force password reset
2. **Enable MFA** → Google Authenticator for `ejay-dev` and Root User
3. **Create IAM Group** → `Developers` + Attach `AmazonS3ReadOnlyAccess`
4. **Write Custom Policy** → `GetCloud101Objects.json` for specific S3 bucket only
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::cloud101-bucket/*"
     }]
   }
---
---
# ⚡ AWS Lambda Architecture 
# Cloud 101
# April 25 2026

[[AWS](https://img.shields.io/badge/AWS-Lambda-FF9900?style=for-the-badge&logo=aws-lambda)](https://aws.amazon.com/lambda/) [[Serverless](https://img.shields.io/badge/Model-Serverless-00C851?style=for-the-badge)](./AWS-Lambda-Architecture.pdf) [[Status](https://img.shields.io/badge/Lab-Complete-00C851?style=for-the-badge)](#)  

[📄 View Architecture Diagram PDF](./AWS-LAMBDA-ARCHITECTURE.pdf)  

### ⚡ **Architecture Flow**  
Event Source [API Gateway/S3/EventBridge] → Lambda Function [hello-world-lambda] → Execution Role → CloudWatch Logs → Target Service [DynamoDB/S3/SNS]  
↑ ↓  
CloudWatch Events Dead Letter Queue  

**Core Rule:** `Event-Driven` → No event = No cost = No server running  

### 🧩 **Components Breakdown**  

| Component | Name Used | Purpose | Best Practice | Boss Analogy |  
| --- | --- | --- | --- | --- |  
| **Event Source** | `API Gateway` | Triggers Lambda | Use REST API | Doorbell sa function |  
| **Lambda Function** | `hello-world-lambda` | Runs code | Python 3.12 + 128MB | Smart microwave |  
| **Execution Role** | `LambdaBasicExecutionRole` | IAM permissions | Least privilege | Worker ID badge |  
| **CloudWatch Logs** | `/aws/lambda/hello-world` | Debug output | Check errors here | CCTV sa function |  
| **Environment Vars** | `TABLE_NAME` | Config without code change | No hardcoded secrets | Settings panel |  
| **Dead Letter Queue** | `lambda-dlq` | Failed events storage | SQS or SNS | Lost and found box |  

### 🛠️ **6 Steps to Build**  
1. **Create Lambda Function** → `hello-world-lambda` with Python 3.12 runtime + Author from scratch  
2. **Set Execution Role** → `LambdaBasicExecutionRole` with `logs:CreateLogGroup` + `logs:PutLogEvents`  
3. **Add Trigger** → API Gateway HTTP API + GET method + Open security  
4. **Write Handler Code** → `def lambda_handler(event, context): return {'statusCode': 200, 'body': 'Hello from Lambda'}`  
```python
import json
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
