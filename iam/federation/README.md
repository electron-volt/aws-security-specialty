# Federation

## AWS Single Sign on (SSO)&#x20;

AWS Single Sign-On is a cloud-based single sign-on (SSO) service that makes it easy to centrally manage SSO access to all of your AWS accounts and cloud applications. Specifically, it helps you manage SSO access and user permissions across all your AWS accounts in AWS Organizations.&#x20;

AWS SSO also helps you manage access and permissions to&#x20;

* commonly used third-party software as a service (SaaS) applications
* AWS SSO-integrated applications&#x20;
* custom applications that support Security Assertion Markup Language (SAML) 2.0.&#x20;

You can also create and manage users directly in the SSO console, so AWS SSO is an identity store itself.&#x20;

## Non-SAML 2.0 compatible user directories

For SAML 2.0 compatible user directories, you can configure SSO directly.

For directories that are not SAML 2.0 compatible, you can create a custom identity broker application to provide SSO. This requires writing some additional code. You can use the GetFederationToken API (or AssumeRole API, which is preferred) to **obtain temporary security credentials**. You can then **construct a custom URL** that your users can use to gain access to AWS. Read more here: [https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_providers\_enable-console-custom-url.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_providers\_enable-console-custom-url.html)

## AWS IAM as identity federation&#x20;

* Can use separate SAML 2.0 or OIDC IdP's for each account
* Enables access control using federated user attributes
* User attributes can be cost center, job role, etc

## Cognito&#x20;

Amazon Cognito handles user authentication and authorization for your web and mobile apps. With user pools, you can easily and securely add sign-up and sign-in functionality to your apps. With identity pools (federated identities), your apps can get temporary credentials that grant users access to specific AWS resources, whether the users are anonymous or are signed in.

* Federation support for web and mobile applications
* Provides sign-in and sign-up
* Supports sign-in with social IdP's such as Google, FaceBook, Apple and Amazon&#x20;
* Supports IdPs using SAML 2.0
