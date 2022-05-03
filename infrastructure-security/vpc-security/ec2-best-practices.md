# EC2 best practices

### Scan for known vulnerabilities

EC2 instances can be scanned for known software vulnerabilities using Amazon Inspector with the “Common vulnerabilities and exposures” assessment and the “Center for Internet Security (CIS) Benchmarks” assessment.

### Quickly patch vulnerable software

Systems Manager Patch Manager can be used to scan EC2 instances, identify vulnerable software, and install patches.

### Allow only approved AMIs

AWS Config can be used to check that EC2 instances have been launched from approved AMIs by using the rule “approved\_ami\_by\_id”.

### Share encrypted EBS snapshot with other account

To securely share encrypted snapshots with a separate AWS account, share the snapshot, use a customer managed KMS key, and allow theDecrypt and CreateGrant actions for the target account in the key policy.

### Secure logging to CloudWatch

An EC2 instance in a private subnet running the unified CloudWatch agent can be configured to send logs to CloudWatch Logs securely via an interface VPC endpoint.

### Layer 4 Ddos attacks&#x20;

Amazon Route 53, AWS Shield, and Elastic Load Balancer can be used to protect EC2 instances against layer 4 DDoS attacks.

### Troubleshoot internet connectivity

Internet connectivity to an EC2 instance relies on correct configuration of security groups, network ACLs, route table entries for an internet gateway, and host-based firewall settings (if applicable).

### Instance metadata v2

You can improve security of the instance metadata service by requiring the use of IMDSv2 by setting the “--metadata-options HttpTokens” option to “required”. This can be done separely for existing and future instances.&#x20;

### Capture traffic for inspection&#x20;

All traffic sent to EC2 instances can be captured for inspection with an intrusion detection appliance by configuring VPC traffic mirroring with a network load balancer.

### **Use AWS Nitro Enclaves for isolation**

AWS Nitro Enclaves is an Amazon EC2 feature that allows you to create isolated execution environments, called _enclaves_, from Amazon EC2 instances. Enclaves are separate, hardened, and highly constrained virtual machines. They provide only secure local socket connectivity with their parent instance. They have no persistent storage, interactive access, or external networking. Users cannot SSH into an enclave, and the data and applications inside the enclave cannot be accessed by the parent instance's processes, applications, or users (including root or admin).
