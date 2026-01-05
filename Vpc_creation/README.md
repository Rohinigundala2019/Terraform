🚀 Terraform AWS VPC Project (Public & Private EC2 Architecture)
📌 Project Overview

This project uses Terraform to provision a production-style AWS infrastructure consisting of a custom VPC, public and private subnets, routing via Internet Gateway and NAT Gateway, and EC2 instances deployed in both subnets.

The goal of this project is to demonstrate real-world AWS networking concepts and Infrastructure as Code (IaC) best practices.

🏗️ Architecture Components
🌐 Networking

VPC: 10.0.0.0/16

Public Subnet: 10.0.1.0/24 (us-east-1a)

Private Subnet: 10.0.2.0/24 (us-east-1b)

🌍 Internet Access

Internet Gateway

Enables inbound/outbound internet access for public subnet

NAT Gateway

Allows private subnet instances to access the internet securely

🛣️ Routing

Public Route Table

Routes 0.0.0.0/0 traffic to Internet Gateway

Private Route Table

Routes 0.0.0.0/0 traffic to NAT Gateway

🖥️ Compute Resources
Public EC2 Instance

Deployed in public subnet

Receives a public IP

Accessible via:

HTTP (port 80)

SSH (port 22)

Used to serve a web application using Apache

Private EC2 Instance

Deployed in private subnet

No public IP

Outbound internet access via NAT Gateway

Designed for backend or internal workloads

🔐 Security
Security Groups

Public Security Group

Allows inbound HTTP (80) and SSH (22) from the internet

Private Security Group

Allows inbound HTTP and SSH only from public subnet

Egress

All outbound traffic allowed

SSH Key Management

SSH key pair is:

Generated using Terraform

Stored locally as a .pem file

Prevents manual key creation and improves automation

🔧 User Data Automation

A single userdata.sh file is used by both EC2 instances

Installs Apache web server

Creates a sample HTML page

Starts and enables the Apache service on boot

This demonstrates code reuse and consistency across infrastructure components.

📁 Project Structure
project/
├── main.tf
├── userdata.sh
├── my-keypair.pem
└── README.md

⚙️ Prerequisites

AWS Account

AWS CLI configured (aws configure)

Terraform installed (v1.3+ recommended)

IAM user with required permissions

🚀 How to Deploy
terraform init
terraform plan
terraform apply


After deployment:

Access public EC2 via browser using its public IP

Private EC2 remains isolated and secure

🎯 Learning Outcomes

By completing this project, you learn:

AWS VPC and subnet design

Public vs private subnet behavior

Internet Gateway vs NAT Gateway

Terraform resource relationships

Secure EC2 deployment

Infrastructure as Code best practices
