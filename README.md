1. Provisioning the EC2 Instance
a. Launching an Ubuntu Server

I began by launching a new EC2 instance using the AWS Management Console.

Instance type: t2.micro (eligible under the free tier)

Operating System: Ubuntu 22.04 LTS

Storage: 8 GB SSD (gp2)

Network: Default VPC

To make the server accessible, I configured the security group to allow inbound traffic on:

Port 22 (SSH) – for secure terminal access

Port 80 (HTTP) – for web traffic

Port 443 (HTTPS) – for secure web traffic

I also tagged the instance for easy identification before launching it. Within minutes, the Ubuntu server was live and ready for configuration.

2. Connecting to the EC2 Instance via SSH

After launching the instance, I connected to it securely using SSH.
I used the private key file (.pem) downloaded during the instance setup and adjusted its permissions with:

chmod 400 privatekeyfile.pem


This ensures only authorized users can access it.
To establish the connection, I executed:

ssh -i privatekeyfile.pem ubuntu@<EC2-Public-IP>


Once connected, I switched to the root user using:

sudo su


From there, I could begin the installation and configuration process for my server.

3. Installing and Configuring Apache Web Server

To install Apache, I ran:

sudo apt-get install apache2 -y


After installation, I verified that the service was running:

sudo systemctl status apache2


The status output confirmed that Apache2 was active and operational, successfully serving web requests on port 80.

4. Installing MariaDB (MySQL) Database

Next, I installed MariaDB, the database engine that WordPress uses to store and manage content:

sudo apt-get install mariadb-server mariadb-client -y


To secure the installation, I ran the built-in security script:

sudo mysql_secure_installation


During the process, I:

Set a password for the root account.

Disabled remote root login.

Removed anonymous users.

Deleted the default test database.

Reloaded privilege tables to apply changes.

These steps hardened the database configuration and minimized potential vulnerabilities.

5. Installing PHP and Required Extensions

With Apache and MariaDB ready, I installed PHP and essential modules required by WordPress:

sudo apt-get install php php-mysql php-gd php-cli php-common -y


This completed the LAMP environment setup, making the server fully capable of running WordPress.

6. Managing Services with Systemd

To ensure all critical services start automatically on reboot, I enabled them using:

sudo systemctl enable mariadb apache2


Then, I restarted the services to apply all configurations:

sudo systemctl restart mariadb apache2


Finally, I confirmed their active status:

sudo systemctl status mariadb apache2


All services were reported as active (running).

7. Installing and Configuring WordPress
a. Downloading WordPress

I downloaded the latest version of WordPress directly from the official website:

wget https://wordpress.org/latest.tar.gz


Then extracted the contents:

tar -xzf latest.tar.gz


The extracted WordPress files were placed into Apache’s web root directory, allowing the CMS to be served to users through the browser.

8. Verifying the Deployment

After completing all configurations, I accessed my EC2 instance’s public IP address in a web browser.
The WordPress installation screen appeared successfully — confirming that the site was live and accessible via AWS.

9. Results

The WordPress site was deployed successfully on AWS using the LAMP stack.
It was responsive, accessible, and performed efficiently on the t2.micro instance. This project validated my ability to manage cloud-based infrastructure, perform Linux server administration, and deploy web applications effectively.
