# Terminology

## Identity&#x20;

There are three kinds of identities in IAM: users, groups and roles. Policies can be attached to identities.&#x20;

### User

An IAM user. Access to AWS may be programmatic with an access key and secret access ID or console access with a username and password.&#x20;

### Group

A group is a collection of IAM users. You can attach a policy to a group, but a group is not an entity - that is, a group cannot authenticate to AWS.

Note: a group cannot be a principal. You cannot reference a group as principal in an IAM policy.&#x20;

### Role

In most cases AWS roles are the optimal solution. The use of a role requires two policies:

* a permission policy: this defines what rights the role has
* a trust policy: this defines who is allowed to assume the role.

#### Service role&#x20;

A role that a service assumes to perform actions. E.g. the execution role of a Lambda function that allows the function to log to CloudWatch.&#x20;

#### Service-linked roles &#x20;

You can create roles specifically for an AWS service. Some AWS services may create service-linked roles automatically when the resource is created. Note: you cannot delete a service-linked role while the service is in use. You cannot revoke the session for a service-linked role. The service may create or delete the role itself.&#x20;

#### Chained role

Yo dawg I heard you like roles so I had your AWS role assume an AWS role so you can assume a role that assumed a role.&#x20;

Normally when you assume a role, the duration of the role session is set by `DurationSeconds`. With chained roles however, the maximum session length is always 1 hour.&#x20;

## Entity

An entity is an IAM resource object that AWS uses for authentication. These include users and assumed roles.&#x20;

## Principal

A person or application that uses the AWS account root user, an IAM user, or an IAM role to sign in and make requests to AWS. Principals include federated users and assumed roles.&#x20;
