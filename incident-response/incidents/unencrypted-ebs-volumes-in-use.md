# Unencrypted EBS volumes in use

You can create Amazon Machine Images (AMIs) that make use of encrypted EBS boot volumes and use the AMIs to launch EC2 instances. The stored data is encrypted, as is the data transfer path between the EBS volume and the EC2 instance. The data is decrypted on the hypervisor of that instance on an as-needed basis, then stored only in memory. This feature aids your security, compliance, and auditing efforts by allowing you to verify that all of the data that you store on the EBS volume is encrypted, whether it’s stored on a boot volume or on a data volume. Further, because this feature makes use of AWS KMS, you can track and audit all uses of the encryption keys.&#x20;

There are two methods to ensure that EBS volumes are always encrypted. You can verify that the encryption flag as part of the CreateVolume context is set to “true” through an IAM policy. If the flag is not “true” then the IAM policy can prevent an individual from creating the EBS volume. The other method is to monitor the creation of EBS volumes. If a new EBS volume is created, CloudTrail will log an event. A Lambda function can be triggered by the CloudTrail event to check if the EBS volume is encrypted or not, and also what KMS key was used for the encryption.&#x20;

An AWS Lambda function can respond to the creation of an unencrypted volume in several different ways.&#x20;

* The function could call the CopyImage API with the encrypted option to create a new encrypted version of the EBS volume and then attach it to the instance and delete the old version.&#x20;
* Some customers choose to automatically delete the EC2 instance that has the unencrypted volume. Others choose to automatically quarantine the instance it by applying security groups that prevent most inbound connections.&#x20;
* It’s also easy to write a Lambda function that posts to an Amazon Simple Notification Service (SNS) topic that alerts administrators to do a manual investigation and intervention.&#x20;

Note that most enforcement responses can—and should—be accomplished programmatically without human intervention.
