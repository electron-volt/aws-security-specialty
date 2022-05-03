# Whitepaper: Edge security

AWS whitepaper \
[https://docs.aws.amazon.com/whitepapers/latest/security-at-the-edge/security-at-the-edge.html](https://docs.aws.amazon.com/whitepapers/latest/security-at-the-edge/security-at-the-edge.html)

## Summary&#x20;

Edge means different things for different customers. Edge can be a mobile app, an oil rig, IoT devices, etc.&#x20;

At the edge, AWS offers services that address the different aspects of edge security, including

* preventive security mechanisms like encryption and access control
* continuous monitoring mechanisms like configuration auditing
* physical security like tamper-evident enclosures.&#x20;

Customers that need to store and process data on premises, or in countries where there is no AWS Region, can do so securely with AWS edge services.&#x20;

### Secure content delivery

Recommended services are CloudFront, Shield, WAF and Route 53.

CloudFront offers security capabilities, including field-level encryption and HTTPS support, seamlessly running with AWS Shield Advanced, AWS WAF, and Amazon Route 53 to protect against multiple types of attacks, including network and application layer DDoS attacks.

### Network security & application layer protection

Edge networks are architected outside of the security perimeters of traditional cloud. Extending security to edge end devices requires network and application security and continuous monitoring, as well as encryption of data in transit and at rest.

There are two important aspects to network and application layer protection at the edge:

* Protections from well-known exploits and attacks that could affect an organization’s applications
* Visibility and control of workloads

### Security best practices

* Implement a strong identity foundation&#x20;
* Enable traceability&#x20;
* Security at all layers
* Automate security best practices
* Secure data at rest and in transit
* Keep people away from data
* Prepare for security incidents.&#x20;
