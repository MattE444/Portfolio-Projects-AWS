# Launch a Static Website on AWS S3

## Introduction
Not going to go into too much depth here or upload any screenshots as this isn't really a portolio project but rather something I need to do to get my portfolio website in place so I might as well document the process.  I'm completing this project within the AWS console.

## AWS Services used
- S3
- Route 53
- Cloudfront
- Certificate Manager

## Steps to complete:
1. Setup S3 bucket 
   - Bucket MUST have the same name as the domain name.
   - Upload website files/objects into bucket.
   - Configure for website hosting:  Disable Block Public Access, Add bucket policy to allow public read access, Enable Static website hosting
   - Test bucket website endpoint
2. Setup Route 53
    - Register a domain (if you need to)
    - Create an A record Alias to connect the domain name to your S3 bucket endpoint
    - Test new domain name in http
3. Create Cloudfront distribution
    - When creating the distribution the origin domain would be the S3 bucket created in step 1 and we want to redirect HTTP to HTTPS
    - You will need to request a TLS Certificate if you do not already have one when you get to that point in the distribution creation wizard.
    - You'll be taken to Certificate Manager to request the certificate and from Certificate Manager you will need create a new CNAME record in Route 53 for cloudfront.
4. Modify Route 53
     - Change the A record alias to connect to cloudfront
     - Test that domain name still brings up website using https now

## Issues
Two issue I ran into while completing this project.
1. Error when registering a domain - Not my fault and not really sure what the problem was but I had to create a ticket with AWS support to have them help me with this.
2. Your S3 bucket must have the same name as your root domain name - For whatever reason I spaced on this and had to recreate a few things trying to figure out why it wouldn't work.

## Conclusion
You likely just came from the very simple website I created with this.
A simple project to start with.

matt-ellingsen.com

