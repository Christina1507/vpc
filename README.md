# Virtual Private Cloud (VPC) with Public and Private Subnets

## Description
This project demonstrates the creation and configuration of an Amazon Virtual Private Cloud (VPC) with public and private subnets to securely deploy AWS resources. The architecture follows AWS best practices for networking, security, and isolation.

---

## Technologies Used
- Amazon VPC
- Public and Private Subnets
- Internet Gateway (IGW)
- NAT Gateway
- Route Tables
- Security Groups
- EC2 (for validation)

---

## Architecture Overview
- A custom VPC with a defined CIDR block
- Public subnet for internet-facing resources
- Private subnet for backend resources
- Internet Gateway to enable internet access for the public subnet
- NAT Gateway to allow outbound internet access for private subnet instances
- Separate route tables for public and private subnets

---

## VPC Configuration Steps

### Step 1: Create VPC
- Created a VPC with CIDR block `10.0.0.0/16`
- Enabled DNS resolution and DNS hostnames

### Step 2: Create Subnets
- Public Subnet: `10.0.1.0/24`
- Private Subnet: `10.0.2.0/24`
- Subnets created in different Availability Zones for high availability

### Step 3: Create and Attach Internet Gateway
- Created an Internet Gateway
- Attached it to the VPC

### Step 4: Configure Route Tables
- Public Route Table:
  - Added route `0.0.0.0/0` → Internet Gateway
  - Associated with public subnet
- Private Route Table:
  - Associated with private subnet

### Step 5: Create NAT Gateway
- Created NAT Gateway in the public subnet
- Allocated an Elastic IP
- Updated private route table:
  - Added route `0.0.0.0/0` → NAT Gateway

### Step 6: Configure Subnet Settings
- Enabled auto-assign public IP for public subnet
- Disabled public IP assignment for private subnet

---

## Validation
- Launched an EC2 instance in the public subnet and verified internet access
- Launched an EC2 instance in the private subnet and verified outbound internet access via NAT Gateway
- Confirmed no direct internet access to private subnet instances

---

## Outcome
- Successfully created a secure and isolated VPC
- Public subnet allows internet-facing access
- Private subnet protects backend resources
- Architecture supports scalable and secure application deployment

---

## Key Learnings
- Understanding VPC networking fundamentals
- Difference between public and private subnets
- Importance of route tables, IGW, and NAT Gateway
- Implementing secure cloud network architecture
