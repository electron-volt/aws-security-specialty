---
description: An overview of AWS directory services.
---

# Directory services

## AWS Managed Microsoft AD&#x20;

A managed implementation of Microsoft Active Directory. When you create a managed AD, AWS creates a high availability pair of Windows server 2012 Domain Controllers in your AWS VPC.&#x20;

AWS Managed Microsoft AD is your best choice if you need **actual Active Directory features** to support AWS applications or Windows workloads, including Amazon Relational Database Service for Microsoft SQL Server. It's also best if you want a **standalone AD in the AWS Cloud that supports Office 365** or you need an **LDAP directory to support your Linux applications**

### Trust with on-premises AD&#x20;

If you already have an on-premises Microsoft AD, you can connect it to AWS over VPN and create a  one-way or two-way trust relationship between your managed AWS AD and the on-premises AD.&#x20;

## Simple AD&#x20;

Simple AD is a stand-alone managed directory that is powered by a Linux-Samba Active Directory compatible server.&#x20;

Use [Simple AD](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/what\_is.html#simplead) if you need a low-scale, low-cost directory with basic Active Directory compatibility that supports Samba 4–compatible applications, or you need LDAP compatibility for LDAP-aware applications.

## AWS AD Connector

You have a self-managed Active Directory on-premises. Your identities are stored in the on-prem AD and you want to allow those users to access AWS.&#x20;

Connect your on-prem AD over VPN to AWS AD Connector. This allows your AD users to authenticate to AWS services and the AWS management console.&#x20;

AD Connector provides federated sign-in to the AWS management console by mapping AD identities to IAM roles.&#x20;

Use [AD Connector](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/what\_is.html#adconnector) if you only need to allow your on-premises users to log in to AWS applications and services with their Active Directory credentials. You can also use AD Connector to join Amazon EC2 instances to your existing Active Directory domain.

## AD Sync

Synchronization between Azure AD/Office 365 and AWS.&#x20;

## Active Directory Federation Services (ADFS)

Federate identities with Azure or Office 365.

To streamline the administration of user access in AWS, organizations can utilize a federated solution with an external directory, allowing them to minimize administrative overhead. Benefits of this approach include leveraging existing passwords and password policies, roles and groups.

[https://aws.amazon.com/blogs/security/aws-federated-authentication-with-active-directory-federation-services-ad-fs/](https://aws.amazon.com/blogs/security/aws-federated-authentication-with-active-directory-federation-services-ad-fs/)

