# Create a Secure VPC with Public/Private Subnets and NAT Gateway

## Introduction
Create a Secure VPC with Public/Private Subnets and NAT Gateway

## AWS Services used
- VPC


## Steps to complete:
1. Create the VPC
   - Name: MySecureVPC
   - IPv4 CIDR: 10.0.0.0/16
2. Create Subnets
   - Select MySecureVPC
   - PublicSubnetA, us-east-2a, 10.0.1.0/24
   - PublicSubnetB, us-east-2b, 10.0.2.0/24
   - PrivateSubnetA, us-east-2a, 10.0.11.0/24
   - PrivateSubnetB, us-east-2b, 10.0.12.0/24
3. Create an Internet Gateway
   - Name: MyIGW
   - Attach to MySecureVPC
4. Create a Route Table for the Public Subnets
   - Name: PublicRT
   - VPC: MySecureVPC
5. Configure Route Table
   - Edit routes: Add Destination: 0.0.0.0/0 Target: Internet Gateway (MyIGW)
   - Edit Subnet associations: Add the public subnets
6. Create NAT Gateway
   - Name: MyNGW
   - VPC: MySecureVPC
   - Elastic IP: Allocate new EIP
7. Create Route Table for Private Subnets
   - Name: PrivateRT
   - VPC: MySecureVPC
8. Configure Route Table
   - Edit routes: Add Destination: 0.0.0.0/0 Target: NAT Gateway (MyNGW)
   - Edit Subnet associations: Add the private subnets
9. Test Public
    - Create EC2 in PublicSubnetA
    - SSH into EC2 - Check
    - Run ping and curl commands - Check
    - Public works
10. Test Private
    - Create EC2 in PrivateSubnetA
    - SSH into EC2 - Fails
    - SSH into public EC2 -> SSH into private EC2 from public - Check
    - Run ping and curl commands - Check
    - Everything works!


## Issues
No issues but slow going as I continually rechecked myself and made sure I understood what I was doing.

## Conclusion
Working with VPC's and allllll that that entails can be confusing and just a lot to understand.  I had to follow the directions a lot more than I'd like to make sure I was doing it right and stopped a lot to figure out why I was doing what I was doing.  I referenced and rewatched some videos from the AWS Certified Solutions Architect Associate course by Stephane Maarek quite a few times to better understand why I was doing what I was doing.
