# SETTING UP A LAMP STACK ON UBUNTU SERVER

This guide will walk you through the process of setting up a LAMP (Linux, Apache, MySQL, PHP) stack on an Ubuntu Server.
Now you might ask, What is Webstack? Lamp stack?
A web stack: what is it? A webstack is a collection of tools and frameworks used in software development. This collection of frameworks and tools has been carefully selected to complement one another in order to produce software that functions properly. These are abbreviations for distinct technologies combined for a particular technology product. Here are a few webstacks below:

- LAMP - (Linux, Apache, MySQL, PHP, Perl, or Python)
- LEMP - (Linux, Nginx, MySQL, PHP, Perl, or Python)
- MERN - (MongoDB, ExpressJS, ReactJS and NodeJS)
- MEAN - (MongoDB, ExpressJS, AngularJS and NodeJS)


## STEP 1: INSTALLING APACHE WEB SERVER AND UPDATING THE FIREWALL

Apache is web server software that is responsible for accepting HTTP requests from visitors and sending them back the requested information in the form of web pages. Or, in simpler terms, it allows visitors to view content on your website. We have other webservers such as Nginx, Lighttpd, etc.

First things first, update and upgrade your Ubuntu server using the following command:

```bash
sudo apt update && sudo upgrade -y
```
Install Apache web server using Ubuntu's package manager, 'apt', so run the command:
```bash
sudo apt install apache2
```
To verify if Apache Web Server has been downloaded successfully and is currently running on your operating system, run the command:
```bash
sudo systemctl status apache2
```
Chances are, once you've run the command to check for Apache HTTP Server (httpd), it might be currently inactive or stopped on your system. The status inactive (dead) indicates that the service is not running.
To start Apache HTTP Server, you can use the following command:
```bash
sudo systemctl start apache2
```
After starting the service, you can check its status again to ensure that it's running properly.
However, if you want Apache HTTP Server to start automatically upon system boot, you can enable it using the command:
```bash
sudo systemctl enable apache2
```
This will ensure that Apache starts automatically whenever the system boots up.

### PORT MAPPING 
Since our EC2 machine's TCP port 22 is open by default for SSH access, we must add a rule to the EC2 setup in order to allow inbound connections through port 80: Allow incoming traffic through port 80.

EC2 → SECURITY GROUPS → EDIT INBOUND RULES.

This ensures we can reach our server both locally and remotely (from any IP address) using the URL source 0.0.0.0/0. Our server is up and operating.
It's time to see how well our Apache HTTP server can handle requests from the Internet at this point. Try to visit the  URL in your preferred web browser: Insert your Public IP address mapped to port 80.

```bash
http://<Public-IP-Address>:80
```



