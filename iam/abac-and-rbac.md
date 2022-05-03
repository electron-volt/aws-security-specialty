# ABAC and RBAC

## ABAC

Attribute-based access control (ABAC) is an authorization strategy that defines permissions based on attributes. In AWS, these attributes are called _tags_.&#x20;

You can attach tags to IAM resources, including IAM entities (users or roles) and to AWS resources. These ABAC policies can be designed to allow operations when the principal's tag matches the resource tag.&#x20;

[https://docs.aws.amazon.com/IAM/latest/UserGuide/access\_iam-tags.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/access\_iam-tags.html)

## RBAC

The traditional authorization model used in IAM is called role-based access control (RBAC). Here role refers to someone's job function, e.g. database administrator, HR manager or accountant, not an AWS IAM role.

In IAM, you implement RBAC by creating different policies for different job functions. You then attach the policies to identities (IAM users, groups of users, or IAM roles).

