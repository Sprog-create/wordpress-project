# 🖥️ AWS WordPress Hosting Project

## 📘 Overview
This project demonstrates how I successfully hosted a **WordPress website** on **Amazon Web Services (AWS)** using the **LAMP stack** (Linux, Apache, MySQL/MariaDB, and PHP).  
The deployment was carried out on an **Ubuntu 20.04 LTS EC2 instance** in the **eu-west-2 (London)** region.

The objective was to:
- Configure and manage AWS cloud infrastructure.  
- Deploy and host a WordPress application.  
- Ensure high availability, accessibility, and reliability.  

---

## 🚀 Introduction
The project involved setting up a complete **LAMP environment** on AWS to host a WordPress application.  

**LAMP Stack Components:**
- **Linux (Ubuntu 20.04 LTS)** – Base operating system  
- **Apache2** – Web server  
- **MariaDB** – Relational database (MySQL alternative)  
- **PHP** – Server-side scripting language  

After configuring the LAMP stack, WordPress was installed and made publicly accessible.  
This project highlights my skills in **AWS resource management**, **Linux system administration**, and **web deployment**.

---

## 🧱 1. Provisioning the EC2 Instance

### a. Launching an Ubuntu Server
Steps taken:
1. Created an **EC2 instance** using the AWS console.  
2. **Instance Type:** t2.micro (Free Tier eligible)  
3. **Operating System:** Ubuntu 22.04 LTS  
4. **Storage:** 8 GB SSD (gp2)  
5. **Network:** Default VPC  

### 🔐 Security Group Configuration
Allowed inbound traffic for:
- **Port 22 (SSH)** – Secure terminal access  
- **Port 80 (HTTP)** – Web traffic  
- **Port 443 (HTTPS)** – Secure web traffic  

Tagged the instance for identification and launched it successfully.

---

## 🔑 2. Connecting to the EC2 Instance via SSH

Used the private key file (`.pem`) to connect securely.  
First, adjusted file permissions:
```bash
chmod 400 privatekeyfile.pem
