**STEP 5 - SETTING UP PHP ON THE WEBSITE**

By default, when using Apache, if you have both an index.html and an index.php file in a directory, the server will display the index.html file first. This feature is useful for displaying maintenance pages in PHP applications. During maintenance, you can create a temporary index.html file with a message for visitors. Since it takes precedence over index.php, it becomes the main page.

Once maintenance is complete, you can easily rename or delete the index.html file, and the regular application page will return. If you want to change this setup and prioritize index.php over index.html, you can edit the /etc/apache2/mods-enabled/dir.conf file. 

Simply rearrange the order of index.php in the Directory using the command:

```bash
sudo vi /etc/apache2/mods-enabled/dir.conf
```
Now, Insert the configuration into the config file created:
```bash
<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
After saving and closing the file, you will need to reload Apache so the changes take effect. Run the command:
```bash
sudo systemctl reload apache2
```
To ensure PHP is installed and configured properly on your server, we'll now proceed to create a PHP script for testing purposes.


Now that you've designated a custom location for hosting your website's files and directories (/var/www/project-lamp/), let's generate a PHP test script to verify that Apache can effectively handle and process requests for PHP files using the command:

```bash
vi /var/www/project-lamp/index.php
```

Now, let's insert our PHP code. Below is a basic PHP code example that prompts the user for their name and greets them. This code displays a form where the user can input their name. When the form is submitted, it checks if the name field is empty. 

If it's not empty, it displays a greeting with the provided name. If the name field is empty, it prompts the user to enter their name. However, you can use yours; what matters is that you confirm it works on our browser.
```php
<!DOCTYPE html>
<html>
<head>
    <title>Greeting Form</title>
</head>
<body>
    <?php
    // Check if the form is submitted
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Get the name from the form
        $name = $_POST["name"];
        // If name is provided, greet the user
        if (!empty($name)) {
            echo "<h1>Hello, $name!</h1>";
        } else {
            echo "<h1>Please enter your name!</h1>";
        }
    }
    ?>
    <form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
        <label for="name">Enter your name:</label>
        <input type="text" id="name" name="name">
        <input type="submit" value="Submit">
    </form>
</body>
</html>
```

Now that the moment of truth has arrived, save the file and refresh your browser page to confirm you can see ![Alt Text](https://imgur.com/a/7IqDIhf)
a basic PHP coded website that prompts the user for their name and greets them. 
