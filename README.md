# AWS Capstone Project

## Overview
This project is the capstone for the AWS Fundamentals Specialization. The goal is to design a **highly available, scalable, and secure** three-tier architecture for a web application that serves client requests over the internet.

## Scenario
The web application processes incoming client requests, queries a **MySQL database**, and returns the requested data. To meet AWS best practices, the solution must leverage **Amazon Virtual Private Cloud (VPC)**, **Amazon Elastic Compute Cloud (EC2)**, **Amazon Relational Database Service (RDS)**, and **Elastic Load Balancing (ELB)** while ensuring high availability, security, and performance.

## Architecture Design
The system is built using a **three-tier architecture**, which consists of:

1. **Networking Layer**  
   - Amazon **VPC** isolates resources securely.
   - **Public and private subnets** are distributed across multiple **Availability Zones (AZs)** for redundancy.
   - **Security Groups and IAM roles** enforce strict access control.

2. **Compute Layer**  
   - **Auto Scaling EC2 instances** run the application in private subnets.
   - **Application Load Balancer (ALB)** distributes incoming traffic efficiently across multiple EC2 instances.
   - EC2 instances are managed via an **Auto Scaling Group** for elasticity and fault tolerance.

3. **Database Layer**  
   - **Amazon RDS (MySQL) with Multi-AZ deployment** ensures database availability and automatic failover.
   - **Private subnet** restricts direct internet access to the database.
   - **Amazon RDS security groups** control inbound traffic.

## Traffic Flow

1. **Client to Application**  
   - Clients send requests to the **ALB** in the public subnet.  
   - The ALB forwards requests to the **EC2 instances** in private subnets.

2. **Application to Database**  
   - The EC2 instances process requests and query the **RDS instance** for data.  
   - The **Multi-AZ RDS deployment** ensures availability during failover scenarios.

3. **Response to Client**  
   - The EC2 instances process the data and return the response to the client through the ALB.

## AWS Services Used

- **Amazon VPC** – Provides network isolation and secure communication.
- **Amazon EC2** – Hosts the web application with scalable compute resources.
- **Elastic Load Balancer (ALB)** – Distributes incoming traffic across EC2 instances.
- **Amazon RDS (MySQL)** – Managed relational database with high availability.
- **IAM Roles & Security Groups** – Control access and permissions.
- **Amazon CloudWatch** – Monitors system performance and health.


## Future Enhancements

- **Implement AWS Lambda** for serverless processing of certain tasks.
- **Use Amazon S3** for static file storage and CloudFront for CDN delivery.
- **Enable AWS WAF** for enhanced web security.
- **Implement AWS Secrets Manager** to manage database credentials securely.
