# Create an RDS MySQL Database and Connect from EC2

## Introduction
I almost skipped this project since I've technically already done something very similar in the project to setup my job tracker app.  Thats DynamoDB instead of RDS and was completed using Elastic Beanstalk so I figured I would do this anyway since there are some differences.  This should be easy.

## AWS Services used
- RDS

## Steps to complete:
1. Create an RDS MySQL Database
   - MySQL engine in Sandbox template
   - Name: mydb
   - db.t3.micro w/ 20 GB storage
   - Default VPC + subnet
   - New Security group
2. Create an EC2 Instance
   - Linux 2023 AMI
   - t3.micro
   - Use existing key-pair
   - Default VPC + subnet
   - New Security Group
3. Security Group Configuration
   - Add a new inbound rule for the newly created db sg
   - type: MYSQL/Aurora
   - source: newly created ec2 sg
4. Install MySQL Client on EC2
   - SSH via Powershell
   - sudo dnf install mariadb105 -y
5. Connect from EC2
   - mysql -h mydb.ctamk6s82cdg.us-east-2.rds.amazonaws.com -u admin -p
   - See screenshot.  Works!!

## Issues
One minor issue. When installing mysql on the EC2 instance I received an error message.  Apparently I needed to install mariadb instead of using the generic command of mysql since that would install an Oracle mysql and Amazon Linux 2023 does not ship Oracle MySQL client packages by default.  Made the switch and no big deal.

## Conclusion
This was a fairly easy project that I completed quickly.  I enjoyed using command line more to ssh into the ec2.  I look forward to learning more of the powershell and bash commands.
