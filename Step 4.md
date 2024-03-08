**STEP 4: SETTING UP A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE**

**What's an Apache Virtual Host and why are we using it?**

Apache Virtual Hosts, also known as virtual hosts (Vhosts), allow the operation of multiple websites (domains) using a single IP address. This enables hosting several websites or domains on a single server. By mapping the user's requested URL to the document's root, different sites can be displayed based on the request.

The default Apache server block in Ubuntu 20.04 is configured to serve files from the /var/www/html directory. While these settings remain unchanged, we'll add our directory alongside the default one.

Using the "mkdir" command, create a directory with the name - project-lamp in the /var/www/html directory as follows:
```bash
mkdir /var/www/html/project-lamp
```

Next, give your current system user ownership of the directory using the command:
```bash
sudo chown -R Project-lamp /var/www/$USER:$USER
```

Next, use your preferred command-line editor to create and open a new configuration file in Apache's sites-available directory using the command:
```bash
sudo vi /etc/apache2/sites-available/project-lamp.conf
```

The command above create a config file in that path's directory, and then we insert the configuration below into the config file.
```bash
<VirtualHost *:80>
    ServerName project-lamp
    ServerAlias www.project-lamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/project-lamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

After saving the config file, you can run the ls command to confirm and show the new file in the sites-available directory
```bash
sudo ls /etc/apache2/sites-available
```

You should see something like this below, with the first two being default, like we explained earlier, and the latter being the config file we just created.
```bash
000-default.conf  default-ssl.conf  project-lamp.conf
```
The Config file we inserted earlier simply means we are instructing Apache to serve project-lamp with /var/www/project-lamp as its web root directory by utilizing this VirtualHost configuration.

To enable the new virtual host, run the command:
```bash
sudo a2ensite project-lamp
```
Run the following to ensure that there are no syntax issues in your configuration file:
```bash
sudo apache2ctl configtest
```
Lastly, restart Apache for these modifications to take effect, run the command:
```bash
sudo systemctl reload apache2
```

The website is now live, although the web root /var/www/project-lamp is currently empty. In order to verify that the virtual host functions as anticipated, create an index.html file at that location with the command:

```bash
sudo sh -c "echo 'LAMP IS LIVE from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html"
```
The command provided above attempts to echo the message "LAMP IS LIVE from hostname" containing hostname and public IP information, into an HTML file located at /var/www/project-lamp/index.html

Now, try opening the URL of your website in your browser by utilizing its IP address or your DNS name on yur browser:
```bash
[<Your-Public-IP-Address>:80] OR [<http://<Your-Public-DNS-Name>:80>]
```
If the content that you wrote with the "echo" command appears in the index.html file, your Apache virtual host is operating as it should. kudos, It worked!

