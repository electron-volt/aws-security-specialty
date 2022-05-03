# ACM

AWS offers two options to customers deploying managed X.509 certificates. Choose the best one for your needs.

1. **AWS Certificate Manager (ACM)**—This service is for enterprise customers who need a secure web presence using TLS. ACM certificates are deployed through Elastic Load Balancing, Amazon CloudFront, Amazon API Gateway, and other integrated AWS services. The most common application of this kind is a secure public website with significant traffic requirements. ACM also simplifies security management by automating the renewal of expiring certificates. _You are in the right place for this service._
2. **ACM Private CA**—This service is for enterprise customers building a public key infrastructure (PKI) inside the AWS cloud and intended for private use within an organization. With ACM Private CA, you can create your own certificate authority (CA) hierarchy and issue certificates with it for authenticating users, computers, applications, services, servers, and other devices.&#x20;

### Managed renewal

ACM provides managed renewal for your Amazon-issued SSL/TLS certificates. This means that ACM will either renew your certificates automatically (if you are using DNS validation), or it will send you email notices when expiration is approaching. These services are provided for both public and private ACM certificates.&#x20;

### Exceptions

Note the following:

* ACM does not provide certificates for anything other than the SSL/TLS protocols.
* You cannot use ACM certificates for email encryption.
* ACM **does not permit you to opt out** of managed certificate renewal for ACM certificates.&#x20;
* Managed renewal is not available for certificates that you import into ACM.
* You cannot request certificates for Amazon-owned domain names such as those ending in amazonaws.com, cloudfront.net, or elasticbeanstalk.com.
* You cannot download the private key for an ACM certificate.
* **No direct certificate for EC2:** You cannot directly install ACM certificates on your Amazon Elastic Compute Cloud (Amazon EC2) website or application. You can, however, use your certificate with any integrated service.&#x20;

### ACM and EC2

You cannot install an ACM certificate on EC2 - except for Nitro Enclaves.&#x20;

AWS Certificate Manager (ACM) for Nitro Enclaves allows you to use public and private SSL/TLS certificates with your web applications and web servers running on Amazon EC2 instances with AWS Nitro Enclaves.
