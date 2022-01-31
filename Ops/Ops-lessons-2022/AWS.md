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

### Virtual Private Cloud (VPC)

### Route53

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

### CloudFront (CF)




