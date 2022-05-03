# VPC connectivity

There are many ways that you can extend your on-premises network to AWS or connect your VPC's within AWS.&#x20;

## Overview

### VPC peering&#x20;

Two VPC's can be peered together. This is a one-to-one relationship. This is a useful option if you only have a few VPC's to connect together.&#x20;

### VPC sharing

VPC sharing is better than peering if you have hundreds or thousands of VPC's. VPC sharing allows customers to share subnets with other AWS accounts within the same AWS Organization.&#x20;

### AWS Client VPN

AWS Client VPN is a managed client-based VPN service that enables you to securely access AWS resources and resources in your on-premises network.

### AWS Site-to-site VPN

By default, instances that you launch into an Amazon VPC can't communicate with your own (remote) network. You can enable access to your remote network from your VPC by creating an AWS Site-to-Site VPN (Site-to-Site VPN) connection, and configuring routing to pass traffic through the connection.

### AWS Transit Gateway

You can connect your virtual private clouds (VPC) and on-premises networks using a transit gateway, which acts as a central hub, routing traffic between VPCs, VPN connections, and AWS Direct Connect connections.&#x20;

### AWS PrivateLink

AWS PrivateLink is a highly available, scalable technology that enables you to privately connect your VPC to services as if they were in your VPC.

### AWS Direct Connect

AWS Direct Connect establishes a dedicated network connection between your on-premises network and AWS. With this connection in place, you can create virtual interfaces directly to the AWS Cloud, bypassing your internet service provider. This can provide a more consistent network experience.

###
