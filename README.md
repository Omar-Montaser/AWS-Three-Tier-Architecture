# AWS-Capstone-Project
AWS Fundamentals Specialization Capstone project. 
Scenario: You have a web application that accepts requests from the internet. Clients can send requests to query for data. When a request comes in, the web application queries a MySQL database and returns the data to the client.

Instructions: Design a three-tier architecture that follows AWS best practices by using services such as Amazon Virtual Private Cloud (Amazon VPC), Amazon Elastic Compute Cloud (Amazon EC2), Amazon Relational Database Service (Amazon RDS) with high availability, and Elastic Load Balancing (ELB). Create an architecture diagram that lays out your design, including the networking layer, compute layer, database layer, and anything else that’s needed to accurately depict the architecture. Write a few paragraphs that explain why you chose the AWS services that you used and how they would support the solution for the given scenario. Your explanation must describe how traffic flows through the different AWS components—from the client to the backend database, and back to the client.

The architecture uses Amazon VPC to isolate resources securely and distribute them across multiple availability zones (AZs) for high availability. 
Application Load Balancer (ALB) distributes incoming traffic evenly across EC2 instances in public & private subnets managed by Auto Scaling, ensuring scalability and fault tolerance. 
Amazon RDS is used for a managed MySQL database with Multi-AZ deployment, providing automatic failover and high availability. 
IAM secures access, and CloudWatch monitors performance and health.

Traffic Flow 
1. Client to Application: Clients send requests to the ALB in the public subnet, which forwards them to healthy EC2 instances in private subnets.
2. Application to Database: EC2 instances query the RDS instance in private subnets to fetch or update data. The RDS instance’s Multi-AZ feature ensures availability during failover.
3. Response to Client: EC2 instances process the data and return the response to the client via the ALB.
