## WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS
### ASW account setup and provisioning an Ubuntu Server
#### Steps
1. Signed up for an AWS account.
2. Logged in as IAM user
3. In the VPC console, I create Security Group
![Project1pix2](https://user-images.githubusercontent.com/74002629/174605346-f0f4b1bc-0e4e-45f7-ac6e-6a49ae27600a.PNG)

4. Launched an EC2 instance
5. I selelected the Ubuntu free tier instance
6. I set the required configurations (Enabled public IP, security group, and key pair) and finally launched the instance.
![project1pix3](https://user-images.githubusercontent.com/74002629/174606543-32845537-efdd-4abe-a903-82a20f3bbb80.PNG)

7. Next I SSH into the instance using Windows Terminal
8. In the Terminal, I typed cd Downloads to navigate to the locxcation of my key-pair.
9. Inside the Downloads directory, I connect to my instance using its Public DNS.
![project1pix4](https://user-images.githubusercontent.com/74002629/174608684-dadf6c62-f32f-4abf-99bf-dd6078bcf279.PNG)
![project1pix5](https://user-images.githubusercontent.com/74002629/174608722-755ce47c-4c8e-475c-a399-43e314235364.PNG)

### INSTALLING APACHE AND UPDATING THE FIREWALL
#### Steps
1. Install Apache using Ubuntu’s package manager ‘apt', Run the following commands: To update a list of packages in package manager:
*sudo apt update*
![Project1pix6](https://user-images.githubusercontent.com/74002629/176584111-c2fd6d3e-d34a-49c1-854c-8ff272d7b7ca.PNG)

2. To run apache2 package installation:
*sudo apt install apache2*
3. Next, verify that Apache2 is running as a service in the OS. run:
*sudo systemctl status apache2*
4. The green light indicates Apache2 is running.
5. ![Project1pix8](https://user-images.githubusercontent.com/74002629/176584784-e6c1af68-19c6-4fdd-8551-10d1a223c33d.PNG)

6. Open port 80 on the Ubuntu instance to allow access from the internet.
7. Access the Apache2 service locally in our Ubuntu shell by running: 
*curl http://localhost:80* or *curl http://127.0.0.1:80* This command would output the Apache2 payload indicating that it is accessible locally in the Ubuntu shell.
8. Next, test that Apache HTTP server can respond to requests from the Internet. Open a browser and type the public IP of the Ubutun instance: *http://3.235.248.184/:80* This outputs the Apache2 default page.
![Project1pix9](https://user-images.githubusercontent.com/74002629/176584558-a98ef686-4ea4-4df6-8d15-d695377c7d89.PNG)




