# Automate Daily Backups Using AWS Lambda + CloudWatch

## Introduction
I'll create a Lambda function that backs up DynamoDB from my job tracker app and then schedule a daily back up via Cloudwatch.

## AWS Services used
- IAM
- Lambda
- Cloudwatch

## Steps to complete:
1. Create an IAM policy.
   - See attachments
   - Title: DynamoDBBackupPolicy
2. Create an IAM role
   - Title: lambda-dynamodb-backup-role
   - Attach IAM policy created above
   - Also attached AWSLambdaBasicExecutionRole to allow Cloudwatch Logs
3. Create Lambda Function
   - Title: FunctionforAutoBackups
   - Attach 


## Issues


## Conclusion

