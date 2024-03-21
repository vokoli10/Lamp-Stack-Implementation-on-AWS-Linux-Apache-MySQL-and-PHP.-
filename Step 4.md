### STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
#### Steps
1. Setting up a domain called projectlamp. Create the directory for projectlamp using ‘mkdir’. Run: *sudo mkdir /var/www/projectlamp*
2. assign ownership of the directory with your current system user, run: *sudo chown -R $USER:$USER /var/www/projectlamp*
3. Next, create and open a new configuration file in Apache’s sites-available directory. Tpye: *sudo vi /etc/apache2/sites-available/projectlamp.conf*
4. This will create a new blank file. Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:
**<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
  </VirtualHost>**
  ![Project1pix15](https://user-images.githubusercontent.com/74002629/176587989-12ed00f0-f3c5-482f-98dc-1e9c849e8a99.PNG)
  
  5.To save and close the file. Hit the esc button on the keyboard, Type :, Type wq. w for write and q for quit and Hit ENTER to save the file.
  6. use the ls command to show the new file in the sites-available directory: *sudo ls /etc/apache2/sites-available*
  ![Project1pix16](https://user-images.githubusercontent.com/74002629/176588144-f7413246-cf7e-43df-8399-cd7c81e98bae.PNG)
  
  7. Next, use a2ensite command to enable the new virtual host: *sudo a2ensite projectlamp*
  8. Disable the default website that comes installed with Apache. type: *sudo a2dissite000-default*
  9. Esure your configuration file doesn’t contain syntax errors, run: *sudo apache2ctl configtest*
  10. Finally, reload Apache so these changes take effect: *sudo systemctl reload apache2*
  ![Project1pix17](https://user-images.githubusercontent.com/74002629/176588441-b562f1be-f86d-4c35-83a9-1d0294d9eae0.PNG)
  
  11. The website is active, but the web root /var/www/projectlamp is still empty. Create an index.html file in that location so that we can test that the virtual host works as expected:
*sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html*
12. Relaod the public IP to see changes to the apache2 default page.
![Project1pix19](https://user-images.githubusercontent.com/74002629/176588537-7e43b408-6674-4530-afa8-7e65c69800e8.PNG)
 

