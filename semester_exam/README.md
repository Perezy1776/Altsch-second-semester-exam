#Documentation: Provisioning and Deploying a Web Server

##Step 1: Provisioning the Server

###1.1. Choose a Server Provider
-	Select a cloud provider. I used the AWS Cloud Provider
###1.2. Create a New Virtual Machine (VM)
-	Log in to your cloud provider account.
-	Navigate to the section for creating a new instance (e.g., "Launch Instance" on AWS or Select the operating system (I used Ubuntu 20.04 LTS because of its stability).
-	Choose an instance type (select a small instance for a simple HTML site, I chose the t3.micro on AWS).
-	Configure network settings and security groups to allow SSH access.
-	Launch the instance and note the public IP address assigned to it.
###1.3. Connect to the Server
-	Open a terminal (I used termius in my case)
-	Use SSH to connect to the server: ssh username@public-ip-address

##Step 2: Install Apache2 Web Server
###2.1. Update the Package List
-	sudo apt update
###2.2. Install Apache2
-	sudo apt install apache2 
###2.3. Start and Enable Apache2
-	sudo systemctl start apache2
-	sudo systemctl enable apache2
##Step 3: Deploy the HTML Page
###3.1. Prepare Your HTML Files
-	I used nano (linux code editor) for my html files
-	$ sudo nano /var/www/html/index.html
-	Write your HTML file without CSS
###3.2. Set Correct Permissions
-	sudo chmod -R 755 /var/www/html/
##Step 4: Configure Networking
###4.1. Update Firewall Rules
-	Allow HTTP traffic by updating the firewall rules. For Ubuntu with UFW (Uncomplicated Firewall), use:
-	sudo ufw allow 'Apache Full'
###4.2. Configure Apache to Listen on Public IP
-	Ensure your network security group allows inbound traffic on port 80 (HTTP). 
-	Do that by going to security group on AWS instance and setting the inbound rules
###4.3. Test the Setup
-	Open a web browser and enter the public IP address of your server to check if the HTML page is accessible:

##http://13.247.199.161/

