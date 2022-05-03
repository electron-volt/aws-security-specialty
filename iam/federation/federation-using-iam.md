# Federation using IAM

Example: a user in your on-premises network needs to access files stored in an S3 bucket inside AWS.&#x20;

You have an IdP in your on-premises network. There is also an Identity store (LDAP) on-premises.&#x20;

1. Client attempts to authenticate using IdP&#x20;
2. IdP authenticates the user
3. IdP sends client a SAML assertion
4. the client makes API call to **sts:AssumeRoleWithSAML** in AWS&#x20;
5. AWS STS returns temporary credentials to the client
6. the client users the credentials to access AWS services.&#x20;

