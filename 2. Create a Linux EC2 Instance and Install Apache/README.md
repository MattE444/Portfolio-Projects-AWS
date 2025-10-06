# Create a Linux EC2 Instance and Install Apache

## AWS Services used
- ec2
- Instance Connect

## Steps to complete:
1. Create an EC2 instance 
   - I'm using basic Amazon Linux2023 with t3.micro
   - Created a new key pair so I can connect to the instance via SSH
   - Created default 'launch-wizard' security group to allow both SSH and http from anywhere
2. Install Web Server
    - Connect to instance via EC2 Instance Connect
    - Use commands to load and start apache web server httpd
      ```
      sudo yum update -y  # Updates servers packages
      sudo yum install httpd -y  # Installs Apache web server
      sudo systemctl start httpd  # Starts the Apache service
      ```
3. Test the new web server
     - Open web browser and type Public IPv4 for the ec2 instance
     - Should see "It Works!!"

## Issues
Clicking on the "open address" link within the console will attempt to open secure https.  Which obviously won't work if you don't have a secure port open which I didn't. 



