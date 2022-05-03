# CloudTrail



### Organization trails

If you have created an organization in AWS Organizations, you can create a trail that will log all events for all AWS accounts in that organization. This is sometimes referred to as an _organization trail_.

You can also choose to edit an existing trail in the management account and apply it to an organization, making it an organization trail. Organization trails log events for the management account and all member accounts in the organization.

When you create an organization trail, a trail with the name that you give it will be created in every AWS account that belongs to your organization. Users with CloudTrail permissions in member accounts will be able to see this trail when they log into the AWS CloudTrail console from their AWS accounts, or when they run AWS CLI commands such as describe-trail.

However, users in member accounts will not have sufficient permissions to delete the organization trail, turn logging on or off, change what types of events are logged, or otherwise alter the organization trail in any way.

### CloudTrail and S3

To allow delivery of CloudTrail events to an S3 bucket you must ensure the S3 bucket policy grants CloudTrail the s3:PutObject permission and verify that the S3 bucket and prex defined in CloudTrail exists.
