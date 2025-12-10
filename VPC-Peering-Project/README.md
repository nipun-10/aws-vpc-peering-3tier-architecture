# 🚀 3-Tier Architecture with VPC Peering – AWS Project

📌 Overview
This project demonstrates a secure, scalable 3-tier AWS architecture with VPC Peering implemented between two Virtual Private Clouds.
It showcases real-world networking design involving:

Strict network segmentation

Least-privilege security controls

Private inter-VPC communication

Monitoring and observability

This architecture closely mirrors production-grade enterprise environments.

⭐ Project Summary (STAR Format)
S – Situation
To strengthen my AWS networking and architectural fundamentals, I decided to build a fully isolated and secure 3-tier architecture similar to what large-scale enterprises use.

T – Task
Design and deploy a solution with:

Isolated web, app, and db tiers

Secure routing and traffic control

Private VPC-to-VPC connectivity

Health monitoring and performance tracking

A – Action
Created a custom VPC with public and private subnets across AZs

Designed Web, App, and Database tiers with complete isolation

Implemented Security Groups, NACLs, and Route Tables for precise traffic control

Configured VPC Peering to enable secure communication between two VPCs

Built CloudWatch dashboards and alarms for real-time monitoring

Followed AWS best practices for network design, security, and observability

R – Result
Achieved strong tier isolation and secure communication flows

Enabled private cross-VPC traffic using VPC Peering

Improved visibility into system health with CloudWatch monitoring

Strengthened understanding of AWS networking, routing, and security patterns

🧰 AWS Services Used
Service	Purpose
VPC	Core network boundary
Subnets (Public & Private)	Tier separation
Internet Gateway	Public-tier outbound traffic
NAT Gateway	Private-tier internet access
Route Tables	Custom routing logic
Security Groups	Instance-level firewall
Network ACLs	Subnet-level firewall
VPC Peering	Secure cross-VPC communication
CloudWatch Dashboards & Alarms	Monitoring & alerts

🧱 Architecture Layers
🔹 1. Web Tier
Public subnet

Receives incoming traffic

Controlled by SG allowing HTTP/HTTPS

🔹 2. Application Tier
Private subnet

Hosted internal services

Accepts traffic only from Web SG

🔹 3. Database Tier
Highly restricted private subnet

No internet access

Only accessible by Application SG


---

## 🏗️ **Architecture Overview**

Two VPCs were created **manually**:

- **VPC-A (Prod-VPC)**  
  CIDR: `10.0.0.0/16`  
  Subnet: `10.0.1.0/24` (Public)

- **VPC-B (Dev-VPC)**  
  CIDR: `192.168.0.0/16`  
  Subnet: `192.168.1.0/24` (Public)

A **VPC Peering Connection** was created between these two VPCs to enable private communication without using the internet.

---

## 📍 **Region Used**
- `ap-south-1` (Mumbai)

---

## 🔧 **Resources Created Manually**
✔️ VPCs  
✔️ Subnets  
✔️ Internet Gateways  
✔️ Route Tables  
✔️ Security Groups  
✔️ EC2 Instances (one in each VPC)  
✔️ VPC Peering Connection  
✔️ Route Table Propagation (Manual Updates)  
✔️ Connectivity Testing  

---

![VPC Peering GIF](https://raw.githubusercontent.com/nipun-10/vpc-peering/main/VPC-Peering-Project/vpc-peering-image.gif)

vpc-peering-image.gif
## 🔄 **Project Flow / Steps Performed**

### **1️⃣ Create Two VPCs**
- VPC-A (10.0.0.0/16)  
- VPC-B (192.168.0.0/16)

### **2️⃣ Create Subnets**
- Subnet in VPC-A → `10.0.1.0/24`  
- Subnet in VPC-B → `192.168.1.0/24`

### **3️⃣ Attach Internet Gateways**
- Create IGW for each VPC  
- Attach them to VPC-A and VPC-B

### **4️⃣ Configure Route Tables**
- Associate subnets with their respective route tables  
- Add route `0.0.0.0/0` → IGW for internet access

### **5️⃣ Launch EC2 Instances**
- One EC2 instance in VPC-A  
- One EC2 instance in VPC-B  
- Allow SSH (port 22)  
- Allow ICMP (ping)

### **6️⃣ Create VPC Peering Connection**
- Requester: VPC-A  
- Accepter: VPC-B  
- Accept the peering request  
- Check that status becomes **Active**

### **7️⃣ Update Route Tables for Peering**
- In VPC-A Routes → Add route to `192.168.0.0/16` via Peering ID  
- In VPC-B Routes → Add route to `10.0.0.0/16` via Peering ID

### **8️⃣ Modify Security Groups**
- Allow inbound ICMP from the other VPC’s CIDR  
- Allow SSH if required

---

## 🧪 **Connectivity Testing**
- Successfully SSH’d into EC2 instances  
- Ping from **EC2-A → EC2-B** = ✔️ Success  
- Ping from **EC2-B → EC2-A** = ✔️ Success  

This confirms that **VPC Peering is working correctly**, and both instances are communicating privately without using the internet.

---

## 📘 **What I Learned**
- Understanding CIDR planning  
- Creating VPCs & subnets manually  
- How routing tables work  
- Private communication using VPC peering  
- Testing network connectivity  
- AWS networking fundamentals

⭐ Future Enhancements
Add Terraform or CloudFormation templates

Integrate an Application Load Balancer

Add RDS for managed database

Implement AWS WAF & GuardDuty for enhanced security

Automate deployment pipelines with CI/CD

📞 Contact Me
If you'd like to connect, collaborate, or discuss cloud projects:

👤 Name: Nipun Bhardwaj
📧 Email: nipuntyagi983@gmail.com
🔗 LinkedIn: https://www.linkedin.com/in/nipun-bhardwaj-6312a9265/
💻 GitHub: https://github.com/nipun-10

⭐ Support
If you found this project useful, please ⭐ the repository—it helps others discover it!



