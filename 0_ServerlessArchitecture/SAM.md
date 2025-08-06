# AWS Serverless Application
- The [AWS Serverless Application Model (AWS SAM)](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) is an open-source framework that you can use to build serverless applications on AWS.
- A serverless application is a combination of [Lambda functions](../2_Compute/AWSLambda/Readme.md), [event bridge](../4_MessageBrokers/AmazonEventBridge.md), and other resources that work together to perform tasks.
- Note that a serverless application is more than just a Lambda function—it can include additional resources such as APIs, databases, and event source mappings.
- Its also helpful to test [Lambda functions](../2_Compute/AWSLambda/Readme.md).

# SAM features

| Feature          | Description                                                                                                                                                                                                   |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AWS SAM Template | Streamlined Cloudformation template for serverless applications.<br/>- SAM templates are a superset of Cloudformation. <br/>- Any Cloudformation template can be run through SAM unchanged, and it will work. |
| AWS SAM CLI      | Tool for local testing and debugging of serverless applications                                                                                                                                               |
| Deploy           | AWS SAM CLI command for deploying AWS SAM template                                                                                                                                                            |

# References
- [Introducing AWS SAM Pipelines: Automatically generate deployment pipelines for serverless applications](https://aws.amazon.com/blogs/compute/introducing-aws-sam-pipelines-automatically-generate-deployment-pipelines-for-serverless-applications/)
- [How to test serverless functions and applications?](https://docs.aws.amazon.com/lambda/latest/dg/testing-guide.html)