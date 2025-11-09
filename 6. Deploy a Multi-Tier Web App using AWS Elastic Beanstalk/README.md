# Deploy a Multi-Tier Web App using AWS Elastic Beanstalk

## Introduction
The app I'm using I had created by chatGPT in Python.  Its an app to track all of of my job applications.  I'm pushing this project to the front of the line simply because I want to have the job tracker app in place to actually start tracking my applications.  I'll still do the other projects but after I do this one and the next one first.

## AWS Services used
- DynamoDB
- Elastic Beanstalk

## Steps to complete:
1. Create the DynamoDB Table
   - I used the AWS Console to create the table -> DynamoDB -> Create table
   - Table name = JobApplications
   - Capacity = on-demand
2. Create/Package the JobTracker app
   - I had ChatGPT create me a very simple Job Application app in Python/Flask
   - I worked with AI to make sure the app had the correct files and structure
   - Tested it locally to make sure it worked and was what I wanted
   - Zipped up the project for upload.
3. Create Elastic Beanstalk Application
   - I used the AWS Console.  Elastic Beanstalk -> Create Application
   - App name = job-tracker
   - Platform = Python
   - Environment type = Webserver
   - Upload zip file
4. Create Environmental Variables
   - I had to had these manually after everything was finally up and running or I couldn't access the app
   - SECRET_KEY = secret key
   - DYNAMODB_TABLE = JobApplications
   - REGION = US-East-2
5. Check EB Permission to Use DynamoDB
   - Roles were created in the EB Create Application process for this but the roles are pretty broad.
   - Best case would have been to use more of a least necessary kind of permissions although I simply left it as is
6.  Access the APP
   - Yay it works!!

## Issues
I had 2 main issues with completing this.  
- The first one was just getting the application uploaded and the web server started.  It kept telling me that the health was in a degraded state and that the web service was not running.  I had to ultimately make some changes to both the Procfile to update some of the requirement versions and then update the app.py file to create an application = create_app() statements since the app = Flask... statement was inside a function.
- The second issue I had was with getting new applications created.  I was filling out the form and saving it but nothing was happening.  The solution was the with the form validation.  The "Job Link" field expects it to start with http or https and if you type "test link" into that field it fails validation.  

## Conclusion
This was a bit of a challenge as I ran into a few problems I listed above that took some time to work through and understand.  I learned quite a bit about requirements and Procfiles and Gunicorn during the process, however.  I'm also using the console which I know is not normally how this gets done and I look forward to exploring into the world of the command line a bit more.  
I think Elastic Beanstalk is a wonderful tool.  If you've got something that needs to be run on a web server this is a great option to be able to just upload a zip file and have AWS EB do all of the work of figuring out what you need and get it created.




