AWS Cloud 101 Projects
My hands-on labs from AWS Educate at Cebu Eastern College 🚀

Module 4: AWS Core Services

✅ S3 Static Website Hosting
Date: April 20, 2026  
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
AWS EC2 Concepts | April 21, 2026
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

AWS Educate Cloud 101 - Module 4
Ejay Ardimer | Cebu Eastern College
---
---
IT: Linux Basics - chmod | April 21,2026

**Commands Practiced:**
- `touch practice-key.pem` → Created dummy key file
- `chmod 400 practice-key.pem` → Set to read-only permission
- Result: `-r--------` = 400, AWS SSH requirement

**Key Learning:** AWS blocks SSH if .pem file is not 400 permission for security.

**Files:**
- [Linux Basics PDF](./Linux%20basics.pdf)
  ---
  ---
  # AWS RDS MySQL Architecture
### AWS Educate Cloud 101 - Module 4 
### April 23, 2026

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
**Ejay Ardimer | Cebu Eastern College**  
**#AWSEducate #Cloud101 #RDS #MySQL**
