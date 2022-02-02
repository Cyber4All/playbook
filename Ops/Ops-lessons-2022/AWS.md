# AWS Lesson Overview
# Dates: January 14 and 21, 2022
# Instructor: Christopher Wagner

# Outline
## What is AWS?
Amazon Web Service is a major cloud computing platform provided by Amazon. 
AWS offers a plethora of services that are broken into different categories:
* Analytics
* Application Integration
* AR & VR
* Blockchain
* Compute
* Containers
* Database
* Internet of things
* Networking
* Security
* Storage

AWS allows developers to deploy dynamic and static applications, manage user groups and permissions, store files and data, and much more. 
AWS follows a pay-as-you-go model which allows users to only pay for computing time and not for entire services

AWS has regions all across the world and within each region there are availability zones which are one or more discrete data centers.

## AWS Interfaces

There are 3 main interfaces used to communicate with AWS

* AWS Console
* SDKs (Software Development Kits)
* [AWS CLIv2](https://docs.aws.amazon.com/cli/latest/reference/)

### AWS Console

The AWS Management Console is the main place where you can visually see all the AWS Services <br>
The console can lead you to documentation on all the services, training and AWS certifications.


### SDKs

SDKs (Software Development Kits) allows developers to automate AWS tasks in code. <br>
AWS offers SDKs for C++, Go, Java, Javascript, Python3 and many more programming languages <br>
You can find all the [documentation](https://docs.aws.amazon.com/index.html#sdks) for each SDK on the AWS documentation site.

### AWS CLIv2

Finally AWS offers an expansive CLI (Command Line Interface) that allows developers to communicate with any service through the command line. <br>
We use the CLI to deploy our applications on circleCI through the config.yml file <br>
All [documentation](https://docs.aws.amazon.com/cli/?id=docs_gateway) for the AWS CLI can be found on their site

## AWS Services

### Identity and Access Management (IAM)

In short [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) is an access control service that provides ways to organize and manage privileges. <br>

IAM allows you to give different permissions to all your employees in your organizations or anyone outside of your organization. 
The biggest features are User groups, Roles, and Policies

#### User Groups

User Groups are used to groups users in organizations. User Groups have policies attached to them that allow or deny permission to AWS services. In our recent IAM refactor we created multiple user groups. 3 groups for every category (App Integration, Compute, Management, Networking, Security, and Storage) <br>
For example: Compute_1 gives a user full access to AmazonEC2, Administrator access to ElasticBeanstalk, and full access to AWSLambda, while Compute_3 only gives a user read access to these services. For a full breakdown to these user groups, please refer to the google drive document [here](https://docs.google.com/spreadsheets/d/1HKrcq5dDfvAB6Mqk9Ipa6GlcegCP4dWbXRYpjqgsbK8/edit?usp=sharing)

#### Roles

Roles are identities with attached policies that leverage dynamic credentials by making requests to STS.

#### Policies

Policies are attached to users, roles, and user groups. <br>
AWS supports both AWS managed and customer managed policies. An example of AWS managed is AmazonEC2FullAccess 
</br>
Users are also allowed to create their own policies to manage users and user groups. <br>

Each policy contains permissions that give or do not give access to certain services.

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

In short S3 allows customers to store objects into buckets located in a region but are accessible by 'all' regions <br>
You can find S3 documentation [here](https://docs.aws.amazon.com/s3/?id=docs_gateway)

S3 is also called Blob storage. Blobs (or objects) are files

An object is a file and any metadata that describes the file. While a bucket is a container for objects. Each object has a key, which is the unique identifier for the object within the bucket <br>
We use S3 buckets to store static websites, files, and logs.

S3 buckets and the objects inside them are by default, private. You have access only to the S3 resources you created. Access can be granted through bucket policies, bucket ACLs, and IAM policies

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