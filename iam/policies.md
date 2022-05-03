# Policies

## IAM policies

### Identity policy

A policy that is attached to an identity (user, group or role). Identity-based policies grant permissions to the identity that the policy is attached to.&#x20;

#### AWS-managed, customer-managed or inline

AWS have ready policies created by AWS. Customers can write their own customer-managed policies. Inline policies are attached directly to one particular identity and there is a one-to-one mapping between the inline policy and identity.&#x20;

### Resource policy

Resource policies are attached to a resource like an S3 bucket. The resource policy specifies which principals are allowed to take which actions on the resource. All resource policies are **inline** policies. There are no managed resource policies.&#x20;

### Service Control Policy (SCP)

If using AWS Organizations, you can use SCP's to deny actions across the organization. An SCP will also apply to the root user of a member account. An SCP cannot grant any rights, it can only explicitly deny them.&#x20;

### Access Control List (ACL)&#x20;

Access control lists (ACLs) are service policies that allow you to control which principals in another account can access a resource. ACLs cannot be used to control access for a principal within the same account.

### Permission boundary&#x20;

A permissions boundary is an advanced feature for using a managed policy to set the maximum permissions that an identity-based policy can grant to an IAM entity (user or role). An entity's permissions boundary allows it to perform only the actions that are allowed by both its identity-based policies and its permissions boundaries.

#### Privilege escalation

One use case for permission boundaries is avoiding privilege escalation. Imagine a user X who does not have full admin permissions but does have the permissions needed to create users, groups and attach policies. This user X can create a new user Y and put user Y in the Admins group, then log in as the new user Y - performing privilege escalation. With a permission boundary you can enforce that any new user created by user X cannot have more permissions than X, making privEsc impossible.&#x20;
