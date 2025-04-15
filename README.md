### 🧱 Project Architecture

![Architecture Diagram](Structure.webp)



# ☁️ AWS Cloud Lift & Shift Project

This project outlines the complete Lift & Shift process of migrating an on-premise application to AWS Cloud. It includes step-by-step provisioning of infrastructure components like EC2 instances, Auto Scaling Groups, Load Balancer, DNS using Route 53, and network security via Security Groups and Key Pairs. The goal is to replicate the original environment with minimal to no modification to the application code.

---

## 🧭 Project Objective

The **Lift & Shift** model is a cloud migration approach where existing workloads are moved to the cloud **without redesigning or re-architecting** the application. This project demonstrates how to build the equivalent environment in AWS using key cloud services.

---


---

## ⚙️ AWS Services Used

| AWS Service            | Description |
|------------------------|-------------|
| **EC2 Instances**      | Hosts the migrated application (Linux/Windows-based) |
| **Auto Scaling Group** | Automatically scales the number of EC2 instances |
| **Elastic Load Balancer** | Distributes traffic across EC2s |
| **Route 53**           | Provides DNS management and traffic routing |
| **Security Groups**    | Control inbound and outbound traffic to resources |
| **Key Pairs**          | Used for SSH/RDP access to instances |

---

## 🛠️ Prerequisites

- AWS Account with full IAM permissions to create resources
- Key Pair downloaded locally (for SSH access)
- Basic knowledge of networking, EC2, and cloud infrastructure
- An application package to deploy (e.g., WAR, JAR, or binary)

---

## 🔨 Step-by-Step Setup

### 1. **Create Key Pairs**

- Navigate to EC2 Dashboard → Key Pairs → Create key pair
- Save the `.pem` file securely

### 2. **Configure Security Groups**

- Allow access for:
  - Port 22 (SSH) or 3389 (RDP)
  - Port 80/443 (HTTP/HTTPS)
- Limit access by CIDR (e.g., your public IP)

### 3. **Launch EC2 Instances**

- Use pre-configured AMIs (Amazon Linux, Ubuntu, Windows)
- Attach correct Security Group and Key Pair
- Install application dependencies (e.g., Apache Tomcat, Java, etc.)

### 4. **Configure Load Balancer**

- Choose **Application Load Balancer**
- Add EC2 instances or target group
- Define listeners and health checks
- Enable routing to the application port

### 5. **Set Up Auto Scaling Group**

- Create a launch template from your EC2 configuration
- Set minimum, maximum, and desired capacity
- Link ASG with the Load Balancer for auto-registration

### 6. **Set Up Route 53 DNS**

- Register a domain or use an existing one
- Create a hosted zone
- Add an alias record pointing to the Load Balancer DNS

### 7. **Deploy Application**

- Upload WAR/JAR files under `Build and Deploy Artifacts/`
- Deploy to Tomcat or your runtime environment
- Test application via Load Balancer DNS or Route 53 domain

### 8. **Validate Setup**

- Perform functional testing of the deployed app
- Simulate instance failure and observe autoscaling
- Confirm routing via DNS works globally

---

## 📦 Folder Descriptions

- `Autoscaling Group/`: Launch template, ASG policy config, target groups
- `Build and Deploy Artifacts/`: Application binaries and deployment notes
- `DNS Route 53/`: Hosted zone setup, DNS records
- `EC2 Instances/`: AMI details, instance launch instructions
- `Load Balancer & DNS/`: ALB setup guide, listeners, health checks
- `Security Groups & Keypairs/`: Templates and setup scripts
- `Validate & Summarize/`: Final test checklist and summary report

---






