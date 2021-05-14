# Cribl AppScope on Amazon
> This Quick Start guide was created by [Cribl](https://cribl.io) to help the deployment of Cribl [AppScope](https://appscope.dev) in your AWS environment. You can easily deploy the AppScope Lambda function layer in your AWS environment.

## Overview 
Cribl has created a lambda layer that is shared with the community to help debug and understand what is happening with their lambda functions. This layer is a no-code deployment and will just require some simple environment variables to work.  

## Architecture 
The Lambda Layer will leverage AppScope code to setup an LD_Preload and an execution path along with where you want to send the data. 


![Cribl AppScope Deplyoment](https://quickstart-cribl-appscope.s3.amazonaws.com/architecture/AppScope_Lambda.png)

_Figure 1: Cribl AppScope deployment in AWS_

* In AWS: 
   * Lambda Function Layer

## Cost and licenses
You are responsible for the cost of the AWS services used while running this Quick Start reference deployment. There are no additional costs for using the Quick Start. The Cribl LogStream license included in your deployment will default to the LogStream Free 1TB license. For more information about licensing, please refer to the [Cribl LogStream Pricing Page](https://cribl.io/cribl-logstream-pricing/).

> Estimated Infrastructure Cost assuming US East (N.Virginia) and a C5.2xlarge instance is $256.88/month. Prices may different depending on instance type, region and other factors. Please check with your AWS billing reports or use the [AWS Calculator](https://calculator.aws/#/) to more accuratly predict your costs. 

## Planning the deployment

### Specialized knowledge
This Quick Start assumes familiarity with Amazon Lambda Functions, EC2, S3, IAM, Kinesis and CloudFormation. 

### AWS Account
If you don't already have an AWS Account, create one at https://aws.amazon.com and follow the instructions.


## Deployment options
You can either use the shared lambda layer or create your own using the AppScope binaries. 

## Deployment Steps
1. Sign into your AWS Account.

2. Go to your Lambda Functions:
    - Create a new function (or add this to an existing function skip to step 6)

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_01.png)

3. Select the HelloWorld function and name it `HelloWorldAppScope`

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_03.png)

4. Create Function

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_04.png)

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_05.png)

5. Add the Lambda layer
- Scroll Down to `Layers`

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_06.png)

- Select `Specify an ARN`
- Add the ARN `arn:aws:lambda:us-east-1:967222283187:layer:appscope:4`

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_07.png)

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_08.png)

6. Click on Edit for the `Environment Variables`

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_09.png)

7. Add the Following Variables
- `LD_PRELOAD` = `libscope.so`
- `SCOPE_CRIBL` = your cribl logstream TCP JSON destination
- `SCOPE_EXEC_PATH` = `/lib/ldscope`

![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_10.png)

8. You're ready to start sending data into Cribl LogStream from Lambda functions:
![Step1](https://quickstart-cribl-appscope.s3.amazonaws.com/screenshots/lambda/appscope_11.png)

## Feedback
Please submit feedback, feature ideas or report bugs using the [Issues](https://github.com/criblio/aws-quickstart-cribl-appscope/issues) section of this GitHub repository. If you would like to submit code, please review the Quick Start Contributor's Guide.

## Remove Deployment

Once you have tested this deployment and would like to remove these artifacts from your deployment, simply remove / delete the Lambda Layer. 

### Cribl Resources
- [AppScope](https://appscope.dev)
- [AppScope Use Cases](https://cribl.io/appscope/)
- [Cribl Community](https://cribl.io/community) 
- [Cribl Resources](https://cribl.io/resources)
- [Cribl Docs on Single Instance Deployments](https://docs.cribl.io/docs/deploy-single-instance)
- [Cribl Docs on Distributed Deployments](https://docs.cribl.io/docs/deploy-distributed)
- [Cribl Docs on sizing and scaling instances](https://docs.cribl.io/docs/scaling)

### AWS resources

* [Getting Started Resource Center](https://aws.amazon.com/getting-started/)
* [AWS General Reference](https://docs.aws.amazon.com/general/latest/gr/)
* [AWS Glossary](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html)

### AWS services

* [AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
* [Amazon EC2](https://aws.amazon.com/ec2/)
* [IAM](https://docs.aws.amazon.com/iam/)
* [Amazon VPC](https://docs.aws.amazon.com/vpc/)
* [Amazon Kinesis](https://docs.aws.amazon.com/kinesis/)
