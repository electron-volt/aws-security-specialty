# Best practices

### Do not use root for anything

When an AWS account is first created, the user account used to create the account is called the root. This account should not be used for daily tasks. You will still need root access to for example delete the account in the future.

### Use MFA

Use multi-factor authentication for all users. MFA can be virtual (an authenticator application on your phone, typically) or a physical hardware device. Physical hardware devices have to be purchased from a 3rd party.&#x20;

### Use roles

Whenever possible use roles. Instead of hard-coding access keys in EC2 instances, use instance profiles. Use roles for AWS services as well as AWS users.&#x20;

### Remove unused accounts

You can download a credential report from AWS that shows the age of passwords and access keys. Remove user accounts that are not needed.&#x20;

### Rotate access keys and passwords

An IAM user can have two active access key pairs simultaneously. This is so that you could first create a new access key, then configure any service that uses those keys to use the new keys and only then delete the old key. Use Credential report to find unused accounts or passwords and keys that need to be changed.&#x20;

### If unsure, use managed policies

There are AWS managed policies readily available or you can create your own custom policies. If you are not absolutely certain of the logic of the policy, then it is best to use managed policies if they suit your use case. Otherwise the custom policies can have unintended side effects.&#x20;

