# Load balancing

## NLB

* An NLB does not have a security group associated with it&#x20;
* Use NLB IP addresses when allowing traffic to instances in target groups, not the DNS name
* If health checks are failing for EC2 instances behind an NLB check that the **** instance security groups, and subnet network ACLs allow traffic from the NLB IP addresses.

## ALB

* To ensure that TLS traffic to an ALB is secure even if the certificate private key is compromised you should create an HTTPS listener with a predefined security policy that supports forward secrecy (FS).
* You can redirect HTTP connections to HTTPS on an ALB by creating both types of listener and a rule that redirects HTTP to HTTPS.
* You can add a custom header in CloudFront origin settings to restrict access to a specific ALB with a conditional rule on the ALB looking for the header value.
