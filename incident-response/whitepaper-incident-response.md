# Whitepaper: Incident response

AWS Whitepaper:&#x20;

{% embed url="https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/welcome.html" %}

## Summary

### Foundation of incident response

* **Educate** your security operations and incident response staff about cloud technologies and how your organization intends to use them.
* **Prepare** your incident response team to detect and respond to incidents in the cloud.
* **Simulate** both expected and unexpected security events within your cloud environment
* **Iterate** on the outcome of your simulation to improve the scale of your response posture, reduce time to value, and further reduce risk.

### Incident domain&#x20;

There are three domains within the customer's responsibility where security incidents might occur: service, infrastructure, and application. Consider these domains:

* **Service Domain** – Incidents in the service domain affect a customer's AWS account, IAM permissions, resource metadata, billing, and other areas. A service domain event is one that you respond to exclusively with AWS API mechanisms, or where you have root causes associated with your configuration or resource permissions, and might have related service-oriented logging.
* **Infrastructure Domain** – Incidents in the infrastructure domain include data or network-related activity, such as the traffic to your Amazon EC2 instances within the VPC, processes and data on your Amazon EC2 instances, and other areas, like containers or other future services. Your response to infrastructure domain events often involves retrieval, restoration, or acquisition of incident-related data for forensics. It likely includes interaction with the operating system of an instance, and in some cases, might also involve AWS API mechanisms.
* **Application Domain** – Incidents in the application domain occur in the application code or in software deployed to the services or infrastructure. This domain should be included in your cloud threat detection and response runbooks, and might incorporate similar responses to those in the infrastructure domain. With appropriate and thoughtful application architecture, you can manage this domain with cloud tools, using automated forensics, recovery, and deployment.

### Incident indicators

* Logs and monitoring
* Sudden spikes in billing
* Threat intelligence, if you are subscribed to a 3rd party threat intelligence feed
* AWS support may contact you in case of abuse&#x20;
* Contacts from other parties like your customers, your developers, or other staff in your organization who notice something unusual. This is why it's important to have a well-known, well-publicized method of contacting your security team.

### &#x20;

