# 🍏 Parameter Store

### Parameter Store and KMS&#x20;

To perform any operation on a secure string parameter, Parameter Store must be able to use the Amazon KMS key that you specify for your intended operation. Most of the Parameter Store failures related to KMS keys are caused by the following problems:

* The credentials that an application is using do not have permission to perform the specified action on the KMS key.
* The KMS key is not found. This typically happens when you use an incorrect identifier for the KMS key.
* The KMS key is not enabled. When this occurs, Parameter Store returns an **InvalidKeyId** exception with a detailed error message from Amazon KMS.

### Secure strings and KMS

A secure string is any sensitive data that needs to be stored and referenced in a secure manner. If you have data that you don't want users to alter or reference in clear text, such as domain join passwords or license keys, then specify those values using the Secure String data type. You should use secure strings in the following circumstances:&#x20;

* You want to use data/parameters across AWS services without exposing the values as clear text in commands, functions, agent logs, or CloudTrail logs.&#x20;
* You want to control who has access to sensitive data.&#x20;
* You want to be able to audit when sensitive data is accessed using CloudTrail.&#x20;
* You want AWS-level encryption for your sensitive data and you want to bring your own encryption keys to manage access. By selecting this option when you create your parameter, the Systems Manager encrypts that value when it’s passed into a command and decrypts it when processing it on the managed instance. The encryption is handled by AWS KMS and can be either a default KMS key for the Systems Manager or you can specify a specific CMK per parameter.
