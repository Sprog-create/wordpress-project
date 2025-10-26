# wordpress-project
wordpress website  with hosting it on AWS

AWS-WordPress-Project
This readme file gives a overview explaination as to how I am able to successfully host a WordPress Application using AWS, LAMP stack.

1. Introduction
The project involved me successfully host a WordPress website on an Ubuntu 20.04 LTS EC2 instance running in the eu-west-2 (London) region on Amazon Web Service utilizing the LAMP stack. LAMP is an acronym which stands for Linux operating system, Apache web service, MySQL relational database and PHP and comprises three main components residing on an operating system, in this case, Ubuntu. I then proceed to installed an Apache2 web server on my EC2 Instance along with MariaDB, a public offshoot of MySQL relational database, PHP and WordPress. Apache2 web server was required for hosting the site whilst PHP and MariaDB was required in supporting the functionality of the site. This project was undertaken in order to demonstrate my capability in utilizing AWS resources and my Linux Administrator skills. The key goals for this project were to ensure that the WordPress site had to be highly accessible at all times and met the meet the minimal performance threshold for reliability.

1.a. Provisioning an EC2 Instance (Ubuntu) on AWS
I began with provisioning an EC2 Instance using EC2 Compute service provided by AWS. I selected the Ubuntu 22.04 LTS t.2 micro instance type and deployed the server in the region closest to me, in this case, eu-west-2 (London). I modified the instance settings for the storage and network configuration ( 8GB SSD gp2 and default VPC). I also added a simple tag in order to identify my resource. I also configured the security group of the instance by setting inbound rules in order to allow SSH, HTTP & HTTPS traffic into my server. This kept port 22, 80 and 443 open for incoming traffic from all hosts (0.0.0.0/0). Once this was completed, I launched the ubuntu server and it was up and running very quickly.

1.b. Connecting to the remote server using SSH
I had created a private key file which enabled me access to my newly configured instance from my local machine. Next, I began to modify the key file using chmod command to ensure that only the authorised user of the private key had relative permissions to use the key. This ensured that the file can use or alter by any other users. To connect to my Ubuntu instance, I established an SSH connect to remotely access the instance over the internet. I started a terminal session and executed the command: "ssh -i privatekeyfile.pem@(your EC2 public ip address)" with root privileges. This allow me to connect to my remote instance on AWS and I was able to begin performing configurations on the instance.

2. Apache Webserver
Once connect to my EC2 Instance, I ran the command "sudo su" using the CLI (Command Line Interface)to obtain root permissions. The next step was to install and configure the Apache webserver onto the EC2 (Ubuntu) Instance.

2.a. Installation
To install the Apache WebServer I ran the command "sudo apt-get install apache2". I agreed to the terms of the installation and the webserver was successfully installed. To verify that command was run, I ran the following command "systemctl status apache2" and it showed me that the Apache webserver service was up and running.

3. MariaDB (MySQL) Database Installation and Configuration
In order to download and install the MariaDB database, I ran the command "sudo apt-get install mariadb-server mariadb-client -y". Once completed, I ran the following command "sudo mysql_secure_installation" to excute the MySQL's security script. This script configures security setting and allows you to:

1.Set a password for root accounts (see how to reset or change MySQL root password) 2.Remove the root accounts accessible from outside the localhost. 3.Remove anonymous-user accounts. 4.Delete the test database, accessible by anonymous users. 5.Reload the user privileges tables.

4. PHP Installation and Configuration
In order to install PHP and the relevant packages on my Ubuntu instance, I ran the following command "sudo apt-get install php php-mysql php-gd php-cli php-common -y" on the CLI. At this point, I had a fully functioning production server running on my AWS cloud with database and webserver services performing effectively.

5. Service management using Systemd
5.a. Enable services
Once the all required services were installed on the Ubuntu instance, I utilize the systemd enable service and ran the command "sudo systemctl enable mariadb-server, apache2, php7.2-fpm".

5.b. Restarting and Checking the services are running
It was important that I restarted all the services and checked if these services were running correctly. I utilize the systemd restart service and ran the command "sudo systemctl restart mariadb-server, apache2, php7.2-fpm". I then checked the status of the services by running the following command "sudo systemctl status mariadb-server, apache2, php7.2-fpm". All the services came back in the active and running state which is what I wanted.

6. WordPress Setup
This is how I installed the WordPress application on my Ubuntu EC2 instance.

6.a: Downloading & Installing Wordpress
In order to download Wordpress, I executed the following command "wget https://wordpress.org/latest.tar.gz". This allow me to download all the WordPress files from the web onto my Ubuntu instance. The downloaded files came as a bunch of compressed files and I had to extracted it by using the tar zxf utility. The wordpress application could now be hosted on my Ubuntu instance and fully accessible to be used.

7. Display WordPress Site
Successfully launched WordPress AWS 1a

8. Improvements
For improvement, I would have configured the WordPress site using NGINX webserver instead of Apache Webserver as NGINX is able to handle multiple requests from users to access the site without overloading due to its nature of being event driven. This would further improve on the first requirement which is to make the site high accessible.
