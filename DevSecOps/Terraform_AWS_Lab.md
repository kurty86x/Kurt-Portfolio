# 📝 Overview
This project demonstrates how I used Terraform to provision a simple AWS environment in a lab setting.

The goal was to learn how Infrastructure‑as‑Code (IaC) works, how Terraform organizes resources, and how to deploy and destroy cloud infrastructure safely and consistently.
--- 

### 🎯 Objectives
- Install and configure Terraform
- Create a VPC, subnets, and an EC2 instance
- Use variables, outputs, and state files
- Understand the Terraform workflow (init → plan → apply → destroy)
- Practice safe, repeatable infrastructure deployment

---

### 🏗️ Lab Environment
- AWS Free Tier account
- IAM user with programmatic access
- AWS CLI configured
- Terraform installed on local machine

---

## 📁 Project Structure
```
terraform-aws-lab/
│── main.tf
│── variables.tf
│── outputs.tf
│── provider.tf
└── docs/
```
---

## 🔧 Provider Configuration
provider.tf

```
provider "aws" {
  region = "us-east-1"
}
```

### 🌐 VPC & Networking
main.tf (VPC + Subnet + IGW)
```
resource "aws_vpc" "lab_vpc" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "public_subnet" {
  vpc_id                  = aws_vpc.lab_vpc.id
  cidr_block              = "10.0.1.0/24"
  map_public_ip_on_launch = true
}

resource "aws_internet_gateway" "igw" {
  vpc_id = aws_vpc.lab_vpc.id
}
```

## 💻 EC2 Instance Deployment
main.tf (EC2)
```
resource "aws_instance" "lab_server" {
  ami           = "ami-0c02fb55956c7d316" # Amazon Linux 2
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.public_subnet.id

  tags = {
    Name = "Terraform-Lab-Server"
  }
}
```

## 🧩 Variables & Outputs
variables.tf
```
variable "instance_type" {
  default = "t2.micro"
}
```
outputs.tf
```outputs.tf
output "public_ip" {
  value = aws_instance.lab_server.public_ip
}
```

## ▶️ Terraform Workflow
### Initialize
```
Command:
terraform init
```

### Preview changes
```
Command:
terraform plan
```

### Apply changes
```
Command:
terraform apply
```

### Destroy infrastructure
```
Command:
terraform destroy
```


---

## 🧪 Validation Checklist
- VPC created
- Subnet created
- EC2 instance running
- Public IP output displayed
- Able to SSH into instance
- Terraform state file created
---

## 🛠️ Troubleshooting
- **Invalid AMI ID  **

  Use region‑specific AMIs:
  ```
  Command:
  aws ec2 describe-images --owners amazon
  ```
- **SSH connection fails**  

  Ensure Security Group allows port 22.

- **Terraform state issues** 
  Delete .terraform folder and re‑init:
  ```
  Command:
  terraform init -upgrade
  ```

---

## 📘 What I Learned
- How Terraform provisions AWS resources
- How to structure IaC projects
- How variables and outputs improve reusability
- How to safely deploy and destroy cloud environments
- How IaC supports DevSecOps automation