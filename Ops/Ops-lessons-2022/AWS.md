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
* AWS CLIv2

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

User Groups can be given to Users in an organizations. User Groups give users certain permissions to certain services. In our recent IAM refactor we created multiple user groups. 3 groups for every category (App Integration, Compute, Management, Networking, Security, and Storage) <br>
For example: Compute_1 gives a user full access to AmazonEC2, Administrator access to ElasticBeanstalk, and full access to AWSLambda, while Compute_3 only gives a user read access to these services. For a full breakdown to these user groups, please refer to the google drive document [here](https://docs.google.com/spreadsheets/d/1HKrcq5dDfvAB6Mqk9Ipa6GlcegCP4dWbXRYpjqgsbK8/edit?usp=sharing)

#### Roles

Roles are an identity you can crate that has specific permissions with credentials that are valid for a short duration.

#### Policies

Policies are attached to users, roles, and user groups. <br>
There are AWS managed polices such as: AmazonEC2FullAccess. Users are also allowed to create their own policies to manage users and user groups. <br>
Each policy contains permissions that give or do not give access to certain services.

### Elastic Container Service (ECS)

### Elastic Computer Cloud (EC2)

### Fargate 

### ElasticBeanstalk (EB)

### Lambda

### Cloudwatch

### EventBridge

### CloudTrail

### Simple Notification Service (SNS)

### Secrets Manager

### Simple Storage Service (S3)

In short S3 allows customers to store objects into buckets located in a region but are accessible by 'all' regions <br>
You can find S3 documentation [here](https://docs.aws.amazon.com/s3/?id=docs_gateway)

An object is a file and any metadata that describes the file. While a bucket is a container for objects. Each object has a key, which is the unique identifier for the object within the bucket <br>
We use S3 buckets to store static websites, files, and logs.

S3 buckets and the objects inside them are by default, private. You have access only to the S3 resources you created. Access can be granted by IAM permissions.

### Virtual Private Cloud (VPC)

### Route53

### Certificate Manager

### API Gateway

### CloudFront (CF)




