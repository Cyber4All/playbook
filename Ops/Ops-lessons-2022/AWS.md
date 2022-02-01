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

#### ElasticBeanstalk Resources:
- Used to easily deploy, monitor, and scale web applications and services
- It provisions and operates the infrastructure your application needs as well as the application stack itself. This allows for developers to spend more time writing code rather than managing and configuring servers, load balancers, networks, and firewalls. 
- Will automatically scale compute resources when traffic is high and scale down when it is low to minimize cost and optimize availability.  

#### SecurEd Use Cases:
- We currently deploy CLARK-Gateway, change-authorship-service, standard-guidelines-service, and cards-service.

#### Documentation:
- [AWS ElasticBeanstalk Service](https://aws.amazon.com/elasticbeanstalk/)
- [AWS ElasticBeanstalk Docs](https://docs.aws.amazon.com/elastic-beanstalk/index.html)

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
  - Most core functionality that were implemented in Lambda have become Fargate instances

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

Route 53 Resources:

- Register new domains to an IP
- Register new subdomains to an IP
- Setup various applications like email and google workspace

SecurEd Use Cases:

- Deploying a new app under a different domain
- Setting up Google Workspace
- Setting up Emails
- Deploying a new app under a subdomain
- All SecurEd services deployed use Route 53

Documentation:

- [AWS Route 53](https://aws.amazon.com/route53/)
- [DNS Record Types](https://www.cloudflare.com/learning/dns/dns-records/)

### Certificate Manager

### API Gateway

#### API Gateway Resources
- This allows for developers to create, publish, maintain, monitor, and secure REST, HTTP, and WebSocket APIs. 
- This services acts as the "front door" for applications that need to access databases, EC2 instances, or AWS Lambda functions. 
- It supports both stateful and stateless APIs

#### SecurEd Use Cases 
- We currently do not use this in our production system, but have a number of old implementations in our AWS environment. 

#### Documentation:
- [Amazon API Gateway Overview](https://aws.amazon.com/api-gateway/)
- [Amazon API Gateway Docs](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)

### CloudFront (CF)

CloudFront Resources:

- Accelerate static website content delivery
- Serve video on demand or live streaming video
- Encrypt specific fields throughout system processing
- Serve private content

SecurEd Use Cases:

- Speed up loading our static sites
  - Example: clark.press, standard guidelines client, CARD client

Documentation:

- [CloudFront Use Cases](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/IntroductionUseCases.html)
- [AWS CloudFront](https://docs.aws.amazon.com/cloudfront/)