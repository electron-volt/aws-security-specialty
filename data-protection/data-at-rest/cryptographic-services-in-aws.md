# Cryptographic services in AWS

We will look at some services in much more detail, but here is a list of some cryptographic services that it is useful to know.&#x20;

## CloudHSM&#x20;

A single-tenant cloud Hardware Security Module that is FIPS 140-2 Level 3 compliant.&#x20;

## Amazon DynamoDB Encryption Client

All DynamoDB tables are encrypted by default using AWS-owned keys. These are keys that customers have no access to and no control over. They are not specific to your AWS account so AWS may use them elsewhere as well.&#x20;

If your data requires more secrecy, then you are able to encrypt it before sending it to AWS. This can be done using the Encryption Client.&#x20;

## KMS

AWS Key Management Service provides tools for generating [root keys](https://docs.aws.amazon.com/crypto/latest/userguide/cryptography-concepts.html#define-root-key) and other [data keys](https://docs.aws.amazon.com/crypto/latest/userguide/cryptography-concepts.html#define-data-key). AWS KMS also interacts with many other AWS services to encrypt their service-specific data.

## Secrets Manager&#x20;

Secrets Manager can store secrets such as database credentials, passwords, API keys or even arbitrary text. Secrets Manager can rotate secrets. It has complete rotation templates for RDS, DocumentDB (not DynamoDB!) and Redshift.&#x20;

## AWS Systems Manager Parameter Store&#x20;

Parameter store provides secure, hierarchical storage for configuration data and secrets management. You can store data such as passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data.

Parameter Store has two tiers: Standard and Advanced. Maximum parameter sizes are 4 KB and 8 KB respectively. Total number of parameters allowed is 10 000 and 100 000 respectively.&#x20;

For automatic rotation, you need to use Secrets Manager.&#x20;
