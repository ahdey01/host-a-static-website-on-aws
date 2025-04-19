![Alt text](/Host-a-Static-Website-on-AWS.png)

---

# 📁 Host a Static Website on AWS

This project demonstrates how to host a **static HTML web application** on AWS, using a secure, scalable, and fault-tolerant architecture. The infrastructure is provisioned using AWS core services and follows DevOps best practices for high availability and automation.

All project assets, including the architecture diagram and deployment scripts, are available in this [GitHub repository](https://github.com/aosnotes77/host-a-static-website-on-aws).

---

## 🛠️ Key AWS Components Used

1. **Virtual Private Cloud (VPC)**  
   - Designed with both **public and private subnets** across two **Availability Zones (AZs)** for resilience and redundancy.

2. **Internet Gateway**  
   - Enables internet connectivity for instances within public subnets.

3. **Security Groups**  
   - Act as virtual firewalls for controlling inbound and outbound traffic.

4. **Public Subnets**  
   - Used for components such as the **NAT Gateway** and **Application Load Balancer (ALB)**.

5. **Private Subnets**  
   - Host the **EC2 web servers** and backend components for better security.

6. **NAT Gateway**  
   - Allows instances in private subnets to access the internet securely.

7. **EC2 Instance Connect Endpoint**  
   - Provides secure remote access to instances in both subnet types.

8. **Application Load Balancer**  
   - Distributes incoming traffic evenly to EC2 instances across AZs.

9. **Auto Scaling Group (ASG)**  
   - Automatically adjusts the number of EC2 instances to handle load changes, improving **scalability**, **fault tolerance**, and **cost-efficiency**.

10. **GitHub**  
    - Serves as a version control and collaboration platform for web files.

11. **AWS Certificate Manager**  
    - Ensures secure HTTPS communication by managing SSL/TLS certificates.

12. **Amazon SNS**  
    - Sends notifications about Auto Scaling activities and system health.

13. **Amazon Route 53**  
    - Handles domain registration and DNS routing.

---

## 📦 Deployment Script Overview

Below is the shell script used to configure an EC2 instance as a web server:

```bash
#!/bin/bash
# Switch to root user
sudo su

# Update all installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Move to Apache root directory
cd /var/www/html

# Install Git
yum install git -y

# Clone the website repository
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git

# Copy all contents to the web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Clean up cloned repo
rm -rf host-a-static-website-on-aws

# Enable and start Apache
systemctl enable httpd
systemctl start httpd
```

---

## 📈 Features

- High Availability across **multiple Availability Zones**
- Secure access through **private subnets** and **EC2 Connect Endpoint**
- Auto-scaling with real-time **SNS notifications**
- **SSL-encrypted** traffic with AWS Certificate Manager
- Fully **version-controlled** using Git and GitHub

---

## 📌 Prerequisites

- AWS account with administrative privileges
- Domain name registered in **Route 53**
- EC2 key pair for secure SSH access
- Basic understanding of VPC, Subnets, and Load Balancers

---

## 📎 Resources

- Architecture diagram and deployment scripts: [Project Repo](https://github.com/aosnotes77/host-a-static-website-on-aws)
- AWS Documentation:  
  [VPCs](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |  
  [EC2](https://docs.aws.amazon.com/ec2/) |  
  [Route 53](https://docs.aws.amazon.com/route53/) |  
  [Auto Scaling](https://docs.aws.amazon.com/autoscaling/)  

---

