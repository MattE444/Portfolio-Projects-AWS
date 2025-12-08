# Automate Daily Backups Using AWS Lambda + EventBridge

## Introduction
I'll create a Lambda function that backs up DynamoDB from my job tracker app and then schedule a daily back up via EventBridge.

## AWS Services used
- IAM
- Lambda
- EventBridge

## Steps to complete:
1. Create an IAM policy.
   - See attachment: DynamoDBBackupPolicy.png
   - Title: DynamoDBBackupPolicy
2. Create an IAM role
   - Title: lambda-dynamodb-backup-role
   - Attach IAM policy created above
   - Also attached AWSLambdaBasicExecutionRole to allow Cloudwatch Logs
3. Create Lambda Function
   - Title: FunctionforAutoBackups
   - Attach new IAM role: lambda-dynamodb-backup-role
   - Add python code for Lambda function.  See attachment: PythonCodeforBackupAutomation.png
4. Create the Event Rule
   - Name: daily-dynamodb-backup
   - Define the schedule: cron(0 6 * * ? *)
   - Target: FunctionforAutoBackups Lambda function
5. Test to make sure it works
   - Create test event in Lambda and run
   - Verify backup created in DynamoDB Backups: Check
   - Verify new Cloudwatch group appears with a log stream


## Issues
No issues

## Conclusion
This was very straightforward and was completed quickly.  Although I have created Lambda functions in the past its good practice and I waded into Eventbridge and Cloudwatch for the first time.  I still find IAM confusing at times so its also good to practice creating policies and roles.
