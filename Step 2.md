### INSTALLING MYSQL
#### Steps
In this step, I install a Database Management System (DBMS) to be able to store and manage data for the site in a relational database.
1. Run ‘apt’ to acquire and install this software, run: *sudo apt install mysql-server*
2. Confirm intallation by typing Y when prompted.
3. Once installation is complete, log in to the MySQL console by running: *sudo mysql*
![Project1pix11](https://user-images.githubusercontent.com/74002629/176585224-e55ca7bb-73a7-464a-9172-7161ba5b434b.PNG)

4. Next, run a security script that comes pre-installed with MySQL, to remove some insecure default settings and lock down access to your database system. run: 
*ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';* then exit MySQL shell by typing exit and enter.
5. Run interactive script by typing: *sudo mysql_secure_installation* and following the instrustions.
6. Next, test that login to MySQL console works. Run: *sudo mysql -p* 
![Project1pix21](https://user-images.githubusercontent.com/74002629/176585784-48ef1dd3-049f-45d1-a7df-884764d14d22.PNG)

