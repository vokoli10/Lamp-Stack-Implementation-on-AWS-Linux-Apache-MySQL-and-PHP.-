**STEP 3: INSTALLING PHP**.

We have MySQL installed to store and handle our data, and Apache installed to serve our content. Now we have to install PHP along side with it's dependecies that will execute code and show dynamic material to the user. 
We'll need php-mysql, a PHP module that enables PHP to interact with MySQL-based databases, in addition to the PHP package. Additionally, libapache2-mod-php is required in order for Apache to handle PHP files. Dependencies for core PHP packages will be installed automatically. 

To install these 3 packages at once, run the command:
```bash
sudo apt install php libapache2-mod-php php-mysql
```
To confirm we have successfully downloaded PHP, we can run the following command to check for the version:
```bash
php --version
```
At this point, your LAMP stack is completely installed and fully operational.
- Linux (Ubuntu)
- Apache HTTP Server
- MySQL
- PHP

It is best to set up a good Apache Virtual Host to hold the files and directories for your website before testing your configuration with a PHP script. Users of the websites will not even know that you have many websites hosted on a single system thanks to virtual hosts.
In the following step, we will configure our first virtual host. I will go into much more detail about why we used the Apache virtual host in the following step. 
