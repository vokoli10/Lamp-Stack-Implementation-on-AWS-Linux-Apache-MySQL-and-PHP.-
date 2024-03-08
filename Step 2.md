## STEP 2: INSTALLING MySQL.
To manage and store data for your website in a relational database, you must install a database management system (DBMS) after starting your web server. 
Since MySQL is a popular relational database management system in PHP settings, we're going to use it for our project. 
In accordance with [link](https://www.statista.com/statistics/809750/worldwide-popularity-ranking-database-management-systems/) MySQL is the second most widely used database management system on the planet.

To install MySQL on your server, run the command:
```bash
Sudo apt install mysql-server -y
```
After installation, it's often recommended that you run a security script that comes preinstalled with MySQL. This script will remove some insecure default settings (not all) and lock down access to your database system.
Start the script by running the command:
```bash
sudo mysql_secure_installation
```
Immediately you will be prompted to **VALIDATE THE PASSWORD COMPONENT**. This is being used to test passwords and improve security. It checks the strength of the password and allows the users to set only those passwords that are secure enough. 

Would you like to set up the **VALIDATE PASSWORD** component?

```bash
Press y|Y for Yes, any other key for No:
```
After selecting your choice, you will be prompted with many options, such as privileges, anonymous users, and test databases. 
Upon completion of all of this, the installation will be secured.

Now let's login to the database with the command:
```bash
sudo mysql
```
And to exit the MySql Database, we use the command:
```bash
exit
```
Now, we have established that the MySQL server is now installed and secured. Next, we will install PHP, the final component in the **LAMP stack**.
