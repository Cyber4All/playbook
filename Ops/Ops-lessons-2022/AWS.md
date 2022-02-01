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
- Abstracted version of cloudwatch events
- Allows users to create rules that initiate events that trigger a target it has set in that rule
- Eventbus is a collection of rules tha triggers targets
- In eventbus an event has an rule and a target
  - Whenever the rule is matched, the target is initiated

SecurEd Use Cases:
- Trigger all scheduled tasks in ECS
- Trigger SNS and bundling service

[AWS CloudTrail](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)

### CloudTrail
- Tracks AWS API calls
- Logs data in S3 buckets
- CloudTrail insights logs unusual API activity
- CloudTrail event history stores all API activity within the last 90 days
  - Who called the action
  - What service was called
  - When the user called the action
  - Where the user called it from

SecurEd Use Cases:
- Debugging user permissions

[AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

### Simple Notification Service (SNS)

### Secrets Manager
- Used to hold secrets for an AWS account

SecurEd Use Cases:
- Store IAM key pairs
- Store Admin credentials
- Store secrets for other non-AWS services
- A middle man for key-rotation-service to move credentials from IAM to secrets manager then to the service that the key needs to be rotated on
- Store any sensitive data used for developmental or production purposes

Documentation:
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)

### Simple Storage Service (S3)

### Virtual Private Cloud (VPC)
- Heart of networking at AWS
- Enables launching of a complete virtual network and mimics a data center
- Uses CIDR notation to describe a users network
- Uses subnets to break up the network and allow users to have certain resources uses specific parts of the network
- Uses private subnets to control resources within the network without internet access with the exception of a NAT gateway to connect to services outside of the VPC
- Uses public subnets to control resources within the network along with the ability to initiate and receive connection from the internet through an internet gateway 
- Network Access Control lists are used to control communication within the network at the subnet level
- Security groups are used to control communication to the network at the virtual private cloud instance level
- Route Tables define where subnet traffic can go based on an IP address

SecurEd Use Cases:
- Launch and manage EC2 instances within a network
- Launch and manage ECS clusters within a network
- Launch and manage elastic beanstalk instances within a network
- Launch and manage elastic load balancer instances within a network
- Allow lambda functions to use internal resources

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