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

Allows the management of containers and applications to run on the cloud.

ECS Resources:

- Clusters
  - Services - 24/7 running applications on EC2 or Fargate
  - Tasks (running/stopped)
  - ECS Instances - Compute power for the Cluster
  - Scheduled tasks - Configured task-definitions that are targets of EventBridge rules
- Task-definitions

SecurEd Use Cases:

- Version control our applications with task-definition families (us-east-1, N. Virginia)
- Scheduled tasks with EventBridge can be found in clusters and run on Fargate
- We have an EC2 instance for the Clark-Services cluster which provides compute power to the ECS services running behind a load-balancer

Documentation:

- [AWS ECS Documentation Home](https://docs.aws.amazon.com/ecs/?id=docs_gateway)
- [AWS ECS Best Practices](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/intro.html)
- [AWS ECS Developer Guide](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)

### Elastic Computer Cloud (EC2)

Provides virtual compute power to run applications

EC2 Resources:

- Instances - configured VM that has network information associated with it
- Images - amazon machine images (VMs)
- Instance type - the size of compute power allotted to the instance

SecurEd Use Cases:

- ECS services are deployed using ECS Instance which is actually a t3.large EC2 instance
- ElasticBeanstalk deploys applications on EC2
- In the EC2 dashboard LoadBalancers and their target groups can be found which are used by ElasticBeanstalk and ECS services

Documentation:

- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/?id=docs_gateway)
- [AWS EC2 User Guide for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- [AWS EC2 API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/Welcome.html)

### Fargate

Serverless, pay-as-you-go compute engine that lets you focus on building applications without managing servers.

[What is Serverless?](https://www.redhat.com/en/topics/cloud-native-apps/what-is-serverless)

Difference between Fargate and EC2:

- Serverless
- Autoscales compute resources
- No infrastructure management
- Image -> Define Compute resources -> Run, Manage applications -> Pay

SecurEd Use Cases:

- Scheduled Tasks in ECS Clusters are deployed on Fargate
- Looking to run low-demand services on Fargate rather then EC2
- scalable high-demand services

Documentation:

- [ECS on AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html)
- [User Guide for AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/userguide/what-is-fargate.html)

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

Used to publish, monitor, configure alarms and manage metrics for our systems. There is a console that allows for quick overview and
access to all cloudwatch resources such as:
- Alarms
- Logs
- Metrics
- Events (moved to EventBridge)
- Application Monitoring
- Insights

SecurEd Usage:
- 18 Log groups to store logs that we have across our AWS account/services
- Metrics can be used to monitor different services as well as custom metrics to monitor for
- 15 alarms that will notify us by email if something is wrong

Documentation:
[AWS Cloudwatch](https://docs.aws.amazon.com/cloudwatch/?id=docs_gateway)

### EventBridge

### CloudTrail

### Simple Notification Service (SNS)

Enabled to allow our applications, end-users, and devices to send and receive notifications.

SNS Resources:
- Topics
    - configuration that will notify subscriptors of the rule
- Subscriptions
    - endpoints used as “targets” for notifications

Usage:
- Used in tandem with EventBridge to trigger an email when a scheduled tasks completes.
    - Example: LO or LO revision is released on CLARK

Documentation:
[AWS SNS](https://docs.aws.amazon.com/sns/?id=docs_gateway)

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

Used to manage, deploy, provision, and renew TLS/SSL certificates for our applicaitons. 

CM Resources:
- List certificates
- Request certificate
- Import certificate
- CertificateAuthority (Not used by us but available)

SecurEd Usage:
- We have certificates for CLARK, CARD, and SecurEd stored

Documentation:
[AWS Certificate Manager](https://docs.aws.amazon.com/acm/?id=docs_gateway)

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
