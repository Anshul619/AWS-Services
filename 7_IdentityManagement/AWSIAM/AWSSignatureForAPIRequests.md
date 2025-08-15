# AWS Signature Version 4 for API requests
- Authentication information that you send in a request must include a signature. 
- [AWS Signature Version 4 (SigV4)](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_sigv.html) is the AWS signing protocol for adding authentication information to AWS API requests. 

# AWS SDK, Cli
- If you use an AWS SDK (see Sample Code and Libraries) or AWS Command Line Interface (AWS CLI) tool to send API requests to AWS, you can skip the signature process, as the SDK and CLI clients authenticate your requests by using the access keys that you provide. 
- **Unless you have a good reason not to (for example - custom script), we recommend that you always use an SDK or the CLI.**.

# Why requests are signed?
- Verify the identity of the requester
- Protect data in transit
- Protect against potential replay attacks