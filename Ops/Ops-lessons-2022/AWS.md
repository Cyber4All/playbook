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

### ElasticBeanstalk (EB)

### Lambda

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
