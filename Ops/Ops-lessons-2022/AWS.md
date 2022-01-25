# AWS Lesson Overview
# Dates: January 14 and 21, 2022
# Instructor: Christopher Wagner

# Outline
## What is AWS?

## AWS Interfaces

### AWS Console

### SDKs

### AWS CLIv2

## AWS Services

### Identity and Access Management (IAM)

### Elastic Container Service (ECS)

### Elastic Computer Cloud (EC2)

### Fargate 

### ElasticBeanstalk (EB)

### Lambda

Lambda Resources:

- Used to execute self contained pieces of code (functions) without a server
- Billed for when it's in use rather then a dedicated server
  - Examples of dedicated servers: ECS, EC2, Elastic Beanstalk
- Multiple ways to execute a Lambda Function:
  - API Endpoint
  - Cron Job
  - CloudWatch EventBridge
- VPCs can be configured
- Cannot be dockerized in the production environment
- Can configure ARNs for authentication
- Serverless framework can be used for local development

SecurEd Use Cases:

- Used to perform functionality that is not core to our system
  - Example: Downloads Test - Tests the downloads of various objects in different statuses and reports errors to MongoDB
- Fargate is being used more then Lambda
  - Most core functionality that were implemented as Lambda have become Fargate instances

Documentation:

- [AWS Lambda](https://docs.aws.amazon.com/lambda/)
- [Cron Jobs and Lambda](https://docs.aws.amazon.com/lambda/latest/dg/services-cloudwatchevents-expressions.html)
- [CloudWatch Events and Lambda](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/RunLambdaSchedule.html)
- [Authenicator ARNs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html)
- [Serverless Framework](https://www.serverless.com/)

### Cloudwatch

### EventBridge

### CloudTrail

### Simple Notification Service (SNS)

### Secrets Manager

### Simple Storage Service (S3)

### Virtual Private Cloud (VPC)

### Route53

### Certificate Manager

### API Gateway

### CloudFront (CF)




