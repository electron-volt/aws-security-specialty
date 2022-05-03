# AWS Organizations

We have mentioned Organizations in passing before. Here are some scenarios that may feature on the exam.&#x20;

### All features enabled

When you set up Organizations, you can opt to only have consolidated billing. The other option is "enable all features". Some features of Organizations that are available only if you enable all features:

* SCP
* SSO&#x20;

### Grant access to all accounts in an AWS Organization in an IAM policy&#x20;

Use principal "\*" and specify the aws:PrincipalOrgId as a condition. This means that the policy applies to all principals in accounts that belong to that specific organization.&#x20;

### Apply one CloudTrail trail to the entire organization, with centralized logging

If you have created an organization in AWS Organizations, you can create a trail that will log all events for all AWS accounts in that organization. This is sometimes referred to as an _organization trail_.

{% embed url="https://docs.aws.amazon.com/awscloudtrail/latest/userguide/creating-trail-organization.html" %}

### AWS Single Sign On for Organizations

AWS SSO is integrated deeply with AWS Organizations and AWS API operations, unlike other cloud native SSO solutions. AWS SSO natively integrates with AWS Organizations and enumerates all your AWS accounts. If you have organized your accounts under organizational units (OUs) you will see them displayed that way within the AWS SSO console. That way you can quickly discover your AWS accounts, deploy common sets of permissions, and manage access from a central location.

### AWS Control Tower

AWS Control Tower can be used for deploying and managing large numbers ofAWS accounts. Control Tower creates a well-architected multi-account baseline known as a landing zone that is based on best practices.

With Control Tower you have preventive guardrails and detective guardrails.&#x20;

* Preventive guardrails are based on SCPs and disallow API actions.&#x20;
* Detective guardrails are implemented using AWS Config rules and Lambda functions that monitor and govern compliance.
