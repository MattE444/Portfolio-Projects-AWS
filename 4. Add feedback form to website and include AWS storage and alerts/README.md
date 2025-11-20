# Add Feedback form to website and include AWS storage and alerts

## Introduction
I decided I wanted to add a feedback form to my website so potential employers can tell me what sort of projects they would want to see.  Also, I suppose anybody who happens to stumble across my page can just send me a message if they want which is cool.  So ultimately I'm looking to alter the website to add a form where users can add their name, email, and comments with a send button.  All of this information would then be sent to both my phone as a text message, my email address and also be stored in a new S3 bucket.

## AWS Services used
- S3
- SES
- Lambda
- IAM
- API Gateway

## Steps to complete:
1. Create the S3 bucket
   - I actually decided to just add a folder within the existing S3 bucket for my website.
   - Named the folder website-feedback-submissions
2. Create an SNS Topic for SMS
   - OK this did not go well.
   - See issues below for more details but we are eliminating the text message part of the project as its a lot more difficult than I would have guessed.
3. SES setup
   - Again I had to register my email address.  I was a little unsure if I was about to go down the same rabbithole as the text messages but thankfully no.
   - Added my email address to SES, was sent a verification email and clicked on the link to complete the registration.
4. Create the Lambda Function
   - Created a simple lambda function
   - Code (python) was added courtesy of ChatGPT again.  I did need to add my email address and S3 location for the submissions archive.
5. Set Lambda IAM permissions
   - Added both S3 and SES full access permissions to the role that was created when I created the Lambda function.
6. Create API Gateway
   - I created an HTTP API
   - Added my Lambda from above for the integration
   - Added a route with method: POST and path: feedback/
7. Add the Form to the Website
   - Again ChatGPT supplied the code for the form and js
   - I also had ChatGPT update both the index.html and style.css code to make everything look the same.
8. Test it all out
   - I had some issues.  See below.  I did also get everything to eventually work.

## Issues
I had a few issues with completing this.  
- My first inclination was to send myself a text everytime someone added feedback to my website.  That was waaaay more problematic then I would have expected.  I attempted to this via the simple notiication service but the only way to do this would have been to create an origination identity and then register myself with the phone company, etc, etc.  I had no idea this would be this difficult and its frustrating that I can't have AWS just text me whenever I get a feedback notice but I guess at the same time I'm glad its not easy for just anyone to span peoples phones with whatever they want.
- Second issue was after I completed everything when I submitted the form nothing would happen.  I ended up having to add some access control options to CORS.  I'm not horribly familiar with CORS although I've been studying it.  Not sure why this wasn't part of the original process.  After adding the access controls though the form would submit...however....
- My third issue was that after submitting the form it nothing happened.  No error messages but also no email and nothing appears in S3.  The problem it turns out was that I forgot to deploy the code in the lambda function.  Duh.  I was going to leave this off but I feel like its important because it happens.  Sometimes its the little things.
- My fourth and last issue was after deploying the code above I received an error message that said the message was not sent.  This turned out to be a problem with the S3 bucket name.  Apparently you cannot direct the message to a folder within your bucket by just using the BUCKET_NAME = "matt-ellingsen.com/website-feedback-submissions/".  The bucket name is just the first part and I had to add a KEY_PREFIX = "website-feedback-submissions/" statement to make that work correctly.  Again something simple that I learned.

## Conclusion

