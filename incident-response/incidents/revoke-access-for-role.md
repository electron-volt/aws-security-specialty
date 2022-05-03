# Revoke access for role

[https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use\_revoke-sessions.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use\_revoke-sessions.html)

You have a role in your AWS account that is used by both legitimate users and now sadly some attacker as well. You want to immediately remove the attacker's access.&#x20;

1. Go to **IAM** > **Roles** > pick the role in question&#x20;
2. On the **Revoke sessions** tab choose **Revoke active sessions.**

This adds the `AWSRevokeOlderSessions` policy to the role. It applies to all active sessions and they are terminated.&#x20;

Cons:

* all legitimate users also lose access

Pros:

* attackers lose access immediately
* The policy does not need to be removed from the role, as it will not affect future users who assume the role.&#x20;



