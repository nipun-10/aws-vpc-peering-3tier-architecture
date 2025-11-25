# 🚀 AWS VPC Peering Project (Manual Setup)

This project demonstrates how to manually create and configure **VPC Peering** between two Virtual Private Clouds (VPCs) on AWS. It covers VPC creation, subnet configuration, routing changes, security settings, and connectivity testing using EC2 instances.

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


