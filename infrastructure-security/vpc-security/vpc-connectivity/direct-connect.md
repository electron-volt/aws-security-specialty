# Direct Connect

AWS Direct Connect links your internal network to an AWS Direct Connect location over a standard Ethernet fiber-optic cable. One end of the cable is connected to your router, the other to an AWS Direct Connect router. With this connection, you can create _virtual interfaces_ directly to public AWS services (for example, to Amazon S3) or to Amazon VPC, bypassing internet service providers in your network path.

### Virtual interfaces

You must create one of the following virtual interfaces to begin using your AWS Direct Connect connection.

* Private virtual interface: A private virtual interface should be used to access an Amazon VPC using private IP addresses.
* Public virtual interface: A public virtual interface can access all AWS public services using public IP addresses.
* Transit virtual interface: A transit virtual interface should be used to access one or more Amazon VPC Transit Gateways associated with Direct Connect gateways.

### Encryption&#x20;

AWS Direct Connect does not encrypt your traffic that is in transit by default. To encrypt the data in transit that traverses AWS Direct Connect, you must use the transit encryption options for that service.&#x20;

With AWS Direct Connect and AWS Site-to-Site VPN, you can combine one or more AWS Direct Connect dedicated network connections with the Amazon VPC VPN. This combination provides an IPsec-encrypted private connection that also reduces network costs, increases bandwidth throughput, and provides a more consistent network experience than internet-based VPN connections.
