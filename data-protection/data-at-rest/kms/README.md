---
description: KMS may also be called default key store.
---

# KMS

KMS or Key Management Service is AWS' managed service for creating and storing cryptographic materials in AWS.&#x20;

## Concepts&#x20;

### KMS keys

An _AWS KMS key_ is a logical representation of an encryption key. In addition to the key material used to encrypt and decrypt data, a KMS key includes metadata, such as the key ID, creation date, description, and key state.

#### Customer managed keys

KMS keys that you create yourself using KMS. You have full control over these keys.&#x20;

Tip: one way to check if a key is managed by you is to use the DescribeKey operation. If in the response the KeyManager field says CUSTOMER, it is a customer managed key.&#x20;

Note about terminology: AWS KMS is replacing the old term customer master key CMK with KMS key. You might still see the abbreviation CMK, but just think KMS key.&#x20;

You have the option to enable rotation of your KMS keys. In this case they will be rotated once every year.

#### Imported keys

Typically you would use KMS to create the encryption keys, but it is also possible to import your own cryptographic materials into KMS.&#x20;

KMS does not offer any automatic rotation of your imported keys. You are still able to rotate them manually.&#x20;

#### AWS managed keys

_AWS managed keys_ are KMS keys in your account created, managed, and used on your behalf by an AWS service integrated with AWS KMS. Some AWS services support only an AWS managed key. Others use an AWS owned key or offer you a choice of KMS keys.

You are able to view these keys, but cannot manage or rotate them or change their key policies.&#x20;

AWS managed keys are automatically rotated every three years. You cannot change this.

#### AWS owned keys

Some AWS services such as DynamoDB are encrypted using AWS owned keys. You the customer cannot view or manage these keys. They may not be particular to your AWS account. They do not cost the customer anything.&#x20;

### Logging

KMS integrates with CloudTrail to log use of KMS for auditing, regulatory and compliance needs.&#x20;

### Key policy

Key policies are the primary way to control access to AWS KMS keys. Every KMS key must have exactly one key policy. The statements in the key policy document determine who has permission to use the KMS key and how they can use it. You can also use IAM policies and grants to control access to the KMS key, but every KMS key must have a key policy.

### Grants

A _grant_ is a policy instrument that allows AWS principals to use KMS keys in cryptographic operations.  When authorizing access to a KMS key, grants are considered along with key policies and IAM policies. Grants are often used for **temporary permissions** because you can create one, use its permissions, and delete it without changing your key policies or IAM policies.

Grants are commonly used by AWS services that integrate with AWS KMS to encrypt your data at rest. The service creates a grant on behalf of a user in the account, uses its permissions, and retires the grant as soon as its task is complete.

Example: you have an encrypted snapshot of an encrypted EBS volume and you want to share the snapshot with another AWS account. You can use kms:CreateGrant to allow the user in another account to decrypt the snapshot.&#x20;

### Alias

Use an _alias_ as a friendly name for a KMS key. For example, you can refer to a KMS key as _test-key_ instead of 1234abcd-12ab-34cd-56ef-1234567890ab.

In AWS KMS, aliases are independent resources, not properties of a KMS key. As such, you can add, change, and delete an alias without affecting the associated KMS key.&#x20;

### Key rotation

The following table shows details about key rotation in KMS for different key types.&#x20;

![table showing key rotation](<../../../.gitbook/assets/image (3).png>)

#### Rotation of imported keys

AWS KMS keys with imported key material are not eligible for automatic rotation. Therefore, a new KMS key must be created with new key material. An Alias is a friendly name for an AWS KMS key and can be updated to point to a different KMS key. This is the most efficient method as it means any applications configured to use the Alias do not need to be updated.

This process is called **manual rotation.** It is also an option if you want to rotate your keys more frequently than with automatic rotation.

### kms:ViaService

The kms:ViaService condition key can be used in a key policy of an AWS KMS key. This condition limits use of an AWS KMS key to requests from specified AWS services. You can specify one or more services in each kms:ViaService condition key. The operation must be a _KMS key resource operation_, that is, an operation that is authorized for a particular KMS key.

### Enabling and disabling keys

You can disable and re-enable the KMS keys that you manage - so not AWS managed or owned keys. When you create a KMS key, it is enabled by default. If you disable a KMS key, it cannot be used in any cryptographic operation until you re-enable it.

Because it's temporary and easily undone, disabling a KMS key is a safe alternative to deleting a KMS key.

### Key deletion&#x20;

KMS cannot be deleted immediately. This is a good thing, because it protects against accidental deletion of encryption keys that could leave you unable to decrypt data. Instead you schedule keys for deletion. The minimum wait period is **** 7 days, the maximum and default is 30 days.&#x20;

During the waiting period, the KMS key status and key state is **Pending deletion**.

* A KMS key pending deletion cannot be used in any cryptographic operations.
* AWS KMS does not rotate the key material of KMS keys that are pending deletion.

After the waiting period ends, AWS KMS deletes the KMS key, its aliases, and all related AWS KMS metadata.

To recover the KMS key, you can cancel key deletion before the waiting period ends. After the waiting period ends you cannot cancel key deletion, and AWS KMS deletes the KMS key.

#### Deletion of asymmetric keys

Asymmetric encryption has a public key and a private key. In KMS the public key can be downloaded and used outside of AWS. It is possible to be in a situation where the private key has been scheduled for deletion while the public key is still being used to encrypt data, which will then be forever lost when the private key is deleted.&#x20;

To avoid this, monitor CloudTrail logs to see if the public key has been downloaded. If it has, instead of deleting the corresponding private key, only disable it.&#x20;

#### Cryptographic erasure

For imported key materials, you are able to perform cryptographic erasure. Cryptographic erasure is when the cryptographic material used to encrypt the data is deleted. This results in the data being unrecoverable as it cannot be decrypted. Imported key materials in KMS can be deleted within 15 minutes.&#x20;

## Security best practices

#### Disable key instead of deleting

Disabled keys can be re-enabled, whereas a deleted key is lost forever (unless a copy is stored outside of KMS).&#x20;

#### Do not grant users CreateKey permissions unless necessary&#x20;

When a user in an AWS account creates a KMS key, that key belongs to the AWS account, not the user. The user is not automatically the owner of the key and the user is not automatically given permissions to manage and use the key, unless those permissions are explicitly granted via an IAM policy or a key policy.&#x20;

However if the user has the CreateKey permission in KMS, they will also have permission to set the key's key policy. This allows the user to give themselves and others pemission to use and manage the KMS key.&#x20;

#### Use key ARN's as Resource in IAM policies

You cannot use a key ID, alias name, or alias ARN to represent a KMS key in the `Resource` field of an IAM policy so you might be tempted to use a wildcard.&#x20;

In a **key policy,** the wildcard character in the `Resource` element represents the KMS key to which the key policy is attached. But in an **IAM policy**, a wildcard character alone in the `Resource` element (`"Resource": "*"`) applies the permissions to all KMS keys in all AWS accounts that the principal's account has permission to use. This might include KMS keys in other AWS accounts, as well as KMS keys in the principal's account.

As a best practice, specify the key ARN of each KMS key to which the permission applies in the `Resource` element of the policy statement. This practice restricts the permission to the KMS keys that principal requires. \
