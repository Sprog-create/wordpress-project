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

Then connected to the server:

ssh -i privatekeyfile.pem ubuntu@<EC2-Public-IP>


After logging in, switched to the root user:

sudo su

🌐 3. Installing and Configuring Apache Web Server

Installed Apache2:

sudo apt-get install apache2 -y


Verified installation:

sudo systemctl status apache2


The Apache service was active and running, ready to handle web requests.

🗃️ 4. Installing MariaDB (MySQL) Database

Installed MariaDB server and client:

sudo apt-get install mariadb-server mariadb-client -y


Secured the installation:

sudo mysql_secure_installation


Configured by:

Setting a root password.

Disabling remote root login.

Removing anonymous users.

Deleting the test database.

Reloading privilege tables.

This ensured the database was properly hardened for production use.

💻 5. Installing PHP and Required Extensions

Installed PHP and necessary modules:

sudo apt-get install php php-mysql php-gd php-cli php-common -y


At this point, the LAMP stack was fully functional.

⚙️ 6. Managing Services with Systemd

Enabled services to start on boot:

sudo systemctl enable mariadb apache2


Restarted services:

sudo systemctl restart mariadb apache2


Verified their status:

sudo systemctl status mariadb apache2


All services were running successfully.

🧩 7. Installing and Configuring WordPress
a. Downloading and Extracting WordPress

Downloaded the latest version:

wget https://wordpress.org/latest.tar.gz


Extracted files:

tar -xzf latest.tar.gz


Moved WordPress to Apache’s web root and configured database connection settings.
After setup, WordPress became accessible through the instance’s public IP.

🌍 8. Verifying Deployment

Opened the EC2 public IP in a web browser — the WordPress installation screen appeared successfully.
This confirmed that the WordPress site was live and fully functional on AWS.

✅ 9. Results

WordPress successfully deployed using the LAMP stack on AWS.

The website was responsive and accessible publicly.

Showcased proficiency in AWS EC2, Linux administration, and web hosting.

🚧 10. Future Improvements

While Apache performed well, future optimization can include migrating to NGINX.
NGINX is an event-driven web server that handles multiple concurrent requests more efficiently.
This would enhance:

Scalability

Performance

High availability

🏁 Conclusion

This project provided practical experience in:

Cloud-based web hosting using AWS

LAMP stack configuration

Server and database management

It successfully demonstrated my capability to deploy, configure, and maintain a WordPress environment on AWS using best DevOps and Linux administration practices.

🧾 Tech Stack Used
Component	Description
AWS EC2	Cloud compute instance for hosting
Ubuntu 20.04 LTS	Operating system
Apache2	Web server
MariaDB	Database engine
PHP	Server-side scripting
WordPress	CMS platform
