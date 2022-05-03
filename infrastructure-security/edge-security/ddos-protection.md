# Ddos protection

AWS whitepaper for Best practices for DDos resiliency:

{% embed url="https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/welcome.html" %}

## Key points

Why protect against DDos? - ensure availability and responsiveness. Avoid unexpected costs.

Infrastructure layer or application layer attacks&#x20;

Some form of ddos protection is automatically included with AWS services (such as Shield basic). Ddos resilience can be improved by architecture choices.&#x20;

Utilize services that operate at edge locations such as CloudFront, Global Accelerator and Route 53 to build comprehensive availability protection against all known infrastructure layer attacks.&#x20;

To defend against application layer attacks, use CloudFront and WAF.&#x20;

Reduce attack surface by

* obfuscating AWS resources. Do not expose them directly to the internet.&#x20;
* using security groups and NACL's to restrict traffic&#x20;
* protecting your origin when using CloudFront&#x20;
* protecting API endpoints.

Gain visibility by using CloudWatch and VPC Flow Logs. Relevant CloudWatch metrics are for Shield Advanced and AWS WAF.
