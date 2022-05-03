# AWS Shield

AWS Ddos protection comes in two varieties: Standard and Advanced.&#x20;

## Shield Standard

All AWS customers benefit from the automatic protections of Shield Standard, at no additional charge. Shield Standard defends against the most common, frequently occurring network and transport layer DDoS attacks that target your website or applications. While Shield Standard helps protect all AWS customers, you get particular benefit with Amazon Route 53 hosted zones, Amazon CloudFront distributions, and AWS Global Accelerator standard accelerators. These resources receive comprehensive availability protection against all known network and transport layer attacks.

## Shield Advanced

For higher levels of protection against attacks, you can subscribe to AWS Shield Advanced. AWS Shield Advanced is a managed service that helps you protect your application against external threats, like DDoS attacks, volumetric bots, and vulnerability exploitation attempts.

### Protected resources

You can use Shield Advanced for advanced monitoring and protection with the following resource types:

* Amazon CloudFront distributions.
* Amazon Route 53 hosted zones.
* AWS Global Accelerator standard accelerators.
* Amazon EC2 Elastic IP addresses. Shield Advanced protects the resources that are associated with protected Elastic IP addresses.
* Amazon EC2 instances, through association to Amazon EC2 Elastic IP addresses.
* The following Elastic Load Balancing (ELB) load balancers:
  * Application Load Balancers.
  * Classic Load Balancers.
  * Network Load Balancers, through associations to Amazon EC2 Elastic IP addresses.

### Capabilities&#x20;

Shield Advanced includes among other things

* WAF integration: Shield Advanced uses WAF web ACL's rules and rule groups as part of its layer 7 protection&#x20;
* Health-based detection
* Enhanced visibility&#x20;
* Centralized management
* Cost protection opportunities: Shield Advanced offers some cost protection against spikes in your AWS bill that might result from a DDoS attack

### When should you use Shield Advanced

Consider implementing Shield Advanced protections for applications where you need any of the following:

* Guaranteed availability for the users of the application.
* Rapid access to DDoS mitigation experts if the application is affected by a DDoS attack.
* Awareness by AWS that the application might be affected by a DDoS attack and notification of attacks from AWS and escalation to your security or operations teams.
* Predictability in your cloud costs, including when a DDoS attack affects your use of AWS services.

\
