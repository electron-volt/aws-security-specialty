# Policy structure

An IAM policy contains the following elements:

* **Version** – Specify the version of the policy language that you want to use. As a best practice, use the latest `2012-10-17` version.
* **Statement** – Use this main policy element as a container for the following elements. You can include more than one statement in a policy.
* **Sid** (Optional) – Include an optional statement ID to differentiate between your statements.
* **Effect** – Use `Allow` or `Deny` to indicate whether the policy allows or denies access.
* **Principal** (Required in only some circumstances) – If you create a resource-based policy, you must indicate the account, user, role, or federated user to which you would like to allow or deny access. If you are creating an IAM permissions policy to attach to a user or role, you cannot include this element. The principal is implied as that user or role.
* **Action** – Include a list of actions that the policy allows or denies.
* **Resource** (Required in only some circumstances) – If you create an IAM permissions policy, you must specify a list of resources to which the actions apply. If you create a resource-based policy, this element is optional. If you do not include this element, then the resource to which the action applies is the resource to which the policy is attached.
* **Condition** (Optional) – Specify the circumstances under which the policy grants permission.

### Example policy&#x20;

Here is an example policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": "arn:aws:ec2:*:*:instance/*",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/Owner": "${aws:username}"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        }
    ]
}
```

This example shows how you might create an identity-based policy that allows an IAM user to start or stop EC2 instances, but only if the instance tag `Owner` has the value of that user's user name. This policy defines permissions for programmatic and console access.
