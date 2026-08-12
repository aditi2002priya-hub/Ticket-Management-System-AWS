# Cloud-Hosted Ticket Management System – AWS

## 📌 Project Overview

A cloud-hosted ticket management application deployed on AWS.

The application allows users to register, log in, access a dashboard, create support tickets, view ticket details, update tickets, and add comments.

The project demonstrates practical experience with AWS networking, compute, database, load balancing, scalability, security, monitoring, and alerting.

---

## 🎯 Project Objectives

- Deploy a working web application on AWS
- Build a public and private network architecture
- Separate application and database layers
- Provide application scalability using Launch Template and Auto Scaling Group
- Provide database high availability using RDS Multi-AZ
- Securely manage EC2 instances using SSM Session Manager
- Monitor AWS resources using CloudWatch
- Configure alerts using SNS

---

## 🏗️ AWS Architecture

The project follows a multi-tier AWS architecture:

*Users → Application Load Balancer → EC2 Application Instances → RDS MySQL*

Supporting AWS services include:

*VPC, Public/Private Subnets, Internet Gateway, NAT Gateway, Route Tables, Security Groups, IAM Role, S3, Launch Template, Auto Scaling Group, SSM Session Manager, CloudWatch and SNS.*

### Architecture Diagram

> Architecture diagram will be added here.

---

## 🌍 AWS Region

*Region:* ap-south-1 – Mumbai

The project resources were deployed in the AWS Mumbai Region.

---

## 🌐 VPC & Network Design

A dedicated *Amazon VPC* was created for the project.

### Network Components

- 2 Public Subnets
- 2 Private Subnets
- Internet Gateway
- NAT Gateway
- Public Route Table
- Private Route Table

### Public Subnets

Public subnets are used for internet-facing components such as the *Application Load Balancer*.

### Private Subnets

Private subnets are used for application and database resources that should not be directly exposed to the internet.

### Internet Gateway

The Internet Gateway provides internet connectivity for the public network path.

### NAT Gateway

The NAT Gateway allows resources in private subnets to make outbound internet connections without directly exposing them to inbound internet traffic.

### Route Tables

- *Public Route Table:* Routes public subnet traffic through the Internet Gateway.
- *Private Route Table:* Provides routing for private resources, including outbound access through the NAT Gateway.

---

🔐 Security Design
Security Groups
Security Group
Inbound Access
Purpose
ALB-SG
HTTP (80) from Internet
Public entry point
App-SG
HTTP (80) from ALB-SG
Application access
RDS-SG
MySQL (3306) from App-SG
Database access

---

This provides controlled communication between the *ALB → EC2 → RDS* layers.

### IAM Role

An IAM Role was created for the EC2 environment to provide controlled AWS permissions without storing AWS access credentials directly inside the application.

### SSM Session Manager

*AWS Systems Manager Session Manager* was used for secure EC2 administration.

It provides instance access without requiring publicly exposed SSH access.

---

## 💻 Application & Compute Layer

### Amazon EC2

Amazon EC2 hosts the ticket management application.

The application uses:

- PHP
- Apache
- Amazon RDS MySQL

### Launch Template

An *EC2 Launch Template* was created to define the configuration used to launch application instances.

### Auto Scaling Group

An *Auto Scaling Group (ASG)* manages the application instances and supports:

- Application scalability
- Instance replacement
- Maintaining application capacity
- Integration with the Application Load Balancer

---

## ⚖️ Application Load Balancer

An *Application Load Balancer (ALB)* is used as the entry point for application traffic.

### Target Group

A Target Group connects the ALB with the application EC2 instances.

The ALB performs health checks and forwards requests to healthy targets.

### Traffic Flow

*User → ALB → Target Group → Healthy EC2 Instance → RDS*

---

## 🗄️ Database Layer

### Amazon RDS MySQL

*Amazon RDS for MySQL* is used as the managed relational database for application data such as users and tickets.

### RDS Multi-AZ

*RDS Multi-AZ* is enabled to provide database high availability and automatic failover support.

---

## 🪣 Amazon S3

An *Amazon S3 bucket* was created as part of the project infrastructure for cloud-based object storage.

It can support application-related files or attachments.

---

## 📊 Monitoring & Alerting

### Amazon CloudWatch

CloudWatch was used to monitor the AWS infrastructure.

The following alarms were configured:

1. *High CPU – EC2/ASG*
2. *High CPU – RDS*
3. *Unhealthy ALB Targets*

### Amazon SNS

An *SNS Topic* was configured for alert notifications.

### Monitoring Flow

*AWS Resource → CloudWatch Alarm → SNS Topic → Notification*

---

## 🎫 Application Features

The ticket management application includes:

- User Registration
- Login
- Dashboard
- Create/Raise Ticket
- View Tickets
- View Ticket Details
- Update Ticket
- Add Comments

---

## 🧪 Testing & Validation

### Application Testing

- Tested application access through the ALB
- Tested user registration and login
- Verified dashboard functionality
- Viewed ticket details
- Tested ticket updates
- Tested ticket comments

### AWS Infrastructure Testing

- Verified ALB Target Group health
- Verified EC2 application connectivity
- Verified EC2-to-RDS connectivity
- Verified public/private routing
- Verified NAT Gateway connectivity
- Verified CloudWatch alarms
- Verified SNS configuration
- Verified SSM Session Manager access

---

## 🛠️ Challenges & Solutions

| Challenge | Solution |
|---|---|
| Application accessibility issues | Checked ALB, Target Group, Security Groups, routing and application configuration |
| Unhealthy ALB targets | Verified application availability and health-check configuration |
| EC2-to-RDS connectivity | Configured the RDS Security Group for required application access |
| Private subnet outbound access | Configured NAT Gateway and private routing |
| Secure EC2 administration | Used SSM Session Manager |
| Application scalability | Used Launch Template and Auto Scaling Group |
| Database availability | Used RDS Multi-AZ |
| Infrastructure monitoring | Configured CloudWatch alarms |
| Alert notifications | Configured SNS |

---

💰 Cost Awareness
Used db.t3.micro for the project environment.
NAT Gateway was used for private subnet outbound connectivity during testing.
After testing, the NAT Gateway and associated Elastic IP were removed to avoid unnecessary ongoing charges.

## 📸 Project Screenshots

Screenshots of the actual working application and AWS infrastructure will be added here.

### Application Screenshots

- Login Page
- Dashboard
- View Ticket
- Ticket Update
- Ticket Comments

### AWS Infrastructure Screenshots

- ALB and Target Group Health
- Auto Scaling Group
- RDS Multi-AZ
- CloudWatch Alarms
- SSM Session Manager

---

## 🧰 AWS Services & Technologies

| Category | Service / Technology |
|---|---|
| Cloud | AWS |
| Region | ap-south-1 – Mumbai |
| Networking | VPC, Public/Private Subnets, Route Tables |
| Connectivity | Internet Gateway, NAT Gateway |
| Load Balancing | Application Load Balancer, Target Group |
| Compute | EC2 |
| Scalability | Launch Template, Auto Scaling Group |
| Database | Amazon RDS MySQL |
| High Availability | RDS Multi-AZ |
| Storage | Amazon S3 |
| Security | IAM, Security Groups |
| EC2 Management | SSM Session Manager |
| Monitoring | Amazon CloudWatch |
| Alerting | Amazon SNS |
| Application | PHP |
| Web Server | Apache |

---

## 💡 Key Skills Demonstrated

- AWS Cloud Architecture
- VPC Networking
- Public & Private Subnet Design
- Internet Gateway & NAT Gateway
- Route Tables
- Security Groups
- IAM Roles
- EC2
- Launch Templates
- Auto Scaling Groups
- Application Load Balancer
- Target Group Health Checks
- Amazon RDS MySQL
- RDS Multi-AZ
- Amazon S3
- SSM Session Manager
- CloudWatch
- SNS
- AWS Infrastructure Troubleshooting

---

## 📚 Key Learning Outcomes

Through this project, I gained practical experience in:

- Designing public and private AWS networks
- Controlling traffic using route tables and security groups
- Connecting ALB, EC2 and RDS
- Deploying applications on EC2
- Using Launch Templates and Auto Scaling
- Implementing RDS Multi-AZ for high availability
- Managing EC2 securely using SSM Session Manager
- Monitoring infrastructure using CloudWatch
- Creating alert workflows using SNS
- Troubleshooting AWS connectivity and application issues

---

## 🚀 Future Enhancements

- HTTPS using AWS Certificate Manager
- AWS WAF for additional web application protection
- Route 53 custom domain
- CloudFront CDN
- Centralized logging
---

## 📌 Project Summary

The *Cloud-Hosted Ticket Management System – AWS* demonstrates a practical deployment of a web application using AWS networking, load balancing, auto scaling, database high availability, secure EC2 management, monitoring, and alerting.

### Project Focus

*AWS Cloud Computing • Cloud Security • Networking • High Availability • Scalability • Monitoring*

### Project Type

*AWS Cloud & Cloud Security Project

👩‍💻 Author

Aditi Priya

AWS Cloud & Cloud Security Enthusiast
