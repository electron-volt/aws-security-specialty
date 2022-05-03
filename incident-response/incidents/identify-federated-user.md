# Identify federated user

Your organization, example.com, has an IAM administrator named Alice and an employee named Bob. Example.com has configured its SAML 2.0–compliant identity provider and AWS to permit federated users such as Bob (email address: b@example.com) to access the AWS Management Console. Bob signs in to the AWS Management Console via SSO using SAML 2.0, and then he terminates an EC2 instance. Alice learns that a user has terminated the EC2 instance, and she needs to identify which federated user terminated the instance. To do this, she has decided to use CloudTrail.

To identify the federated user that terminated the EC2 instance, Alice signs in to the AWS Management Console and performs the following steps:

1. Alice searches the CloudTrail event logs for the eventName called **TerminateInstances.**
2. In the userIdentity section of the event log found in Step 1, Alice determines the Amazon Resource Name (ARN), including the role session name, of the IAM role assumed by the federated user.
3. Alice searches the CloudTrail event logs for the eventName called **AssumeRoleWithSAML** that includes the IAM role’s ARN identified in Step 2.
4. Finally, Alice identifies the **federated user in the username attribute** in the CloudTrail event log she found in Step 3.
