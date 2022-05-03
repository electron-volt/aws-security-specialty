# Monitoring

## Exam scenarios involving monitoring&#x20;

### Check that CloudTrail is enabled

AWS **Config** can be used with the managed rule cloudtrail-enabled to check that **CloudTrail** is enabled**. Systems Manager** automation can be configured for automatic remediation if the rule returns a non-compliant state.&#x20;

### Notification for security group changes

To automatically notify about security group changes use AWS **CloudTrail** with a **CloudWatch** Logs log group and use a metric filter to match security group changes. Use an **SNS** topic to send notifications.

### Alert for users adding bucket policies

You can generate an alert if users add bucket policies by configuring an Amazon **EventBridge** rule that uses the “AWS API Call via CloudTrail” event source and the “s3:PutBucketPolicy” event pattern.
