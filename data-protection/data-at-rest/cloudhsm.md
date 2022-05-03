---
description: CloudHSM may be called custom key store
---

# CloudHSM

CloudHSM is AWS's cloud hardware security module. It is a FIPS 140-2 level 3 compliant key store. CloudHSM will be single-tenant, meaning it is not shared with other AWS accounts or customers.&#x20;

For most users KMS will be fine. If you work in a very regulated field where you need maximal protection and control over your cryptographic materials, then you might need CloudHSM instead.

When you use an HSM from AWS CloudHSM, you can perform a variety of cryptographic tasks:

* Generate, store, import, export, and manage cryptographic keys, including symmetric keys and asymmetric key pairs.
* Use symmetric and asymmetric algorithms to encrypt and decrypt data.
* Use cryptographic hash functions to compute message digests and hash-based message authentication codes (HMACs).
* Cryptographically sign data (including code signing) and verify signatures.
* Generate cryptographically secure random data.

## Key points&#x20;

### HSM users

CloudHSM users like Crypto Officer are created in CloudHSM, not IAM!&#x20;

Unlike most AWS services and resources, you do not use AWS Identity and Access Management (IAM) users or IAM policies to access resources within your cluster. Instead, you use _HSM users_ directly on the hardware security module (HSM) with AWS CloudHSM. The HSM authenticates each HSM user by means of credentials that you define and manage. Each HSM user has a _type_ that determines which operations you can perform on the HSM as that user.

### Monitoring and logging

**CloudTrail**&#x20;

Use CloudTrail to monitor all API calls in your AWS account, including the calls you make to create and delete clusters, hardware security modules (HSM), and resource tags.

**CloudWatch Logs - logs for users and keys!**&#x20;

Use CloudWatch Logs to monitor the logs from your HSM instances, which include events for create and delete HSM users, change user passwords, create and delete keys, and more.

Yes, you read correctly. Normally we'd assume that auditing happens in CloudTrail, but in this case the logs that contain all the info about users and keys - the crucial actions - are in CloudWATCH.
