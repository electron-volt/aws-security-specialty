# VPC peering and sharing

## VPC peering&#x20;

A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account.&#x20;

The peering connection is formed by one VPC sending a request to the other VPC. The owner of the other VPC can then accept the request.&#x20;

For VPC's that are in the same AWS region, security groups of VPC A can be referenced in the security groups of VPC B. This requires that the peering between VPC's A and B is in the active state.&#x20;

### One-to-one relationship

A VPC peering connection is a one to one relationship between two VPCs. You can create multiple VPC peering connections for each VPC that you own, but transitive peering relationships are not supported. You do not have any peering relationship with VPCs that your VPC is not directly peered with.

### Inter-region VPC peering

Two peered VPCs can be in different regions (also known as an inter-region VPC peering connection). Traffic between peered VPC's remains in the private IP space. **All inter-region traffic is encrypted** with no single point of failure, or bandwidth bottleneck. Traffic always stays on the global AWS backbone, and **never traverses the public internet**, which reduces threats, such as common exploits, and DDoS attacks.&#x20;

### Limitations

* The IPv4 CIDR blocks of two peered VPC's cannot overlap
* Only one peering connection can exist between the same two VPCs at the same time
* You cannot connect to or query the Amazon DNS server in a peer VPC
* For inter-region peering:&#x20;
  * You cannot create a security group rule that references a peer VPC security group.

### Edge-to-edge routing not supported

Assume two VPC's called A and B are peered. If VPC A has any of the following

* an Internet Gateway&#x20;
* a NAT device providing internet connectivity to private subnets
* a VPN or Direct Connect connection to a corporate network&#x20;
* a gateway endpoint to S3 or DynamoDB

then VPC B **cannot** use any of the above to access resources on the other side of the connection. For example VPC B cannot reach the internet via VPC A's IGW or NAT.

## VPC sharing&#x20;

VPC peering solves the problem of how to connect from one VPC to another when you only have a few VPCs. Some AWS customers have hundreds and even thousands of VPCs. In that case VPC sharing is a better option.

VPC **sharing** allows customers to share subnets with other AWS accounts within the same AWS Organization. This is a very powerful concept that allows for a number of benefits:

* Separation of duties: centrally controlled VPC structure, routing, IP address allocation.
* Application owners continue to own resources, accounts, and security groups.
* VPC sharing participants can reference security group IDs of each other.
* Efficiencies: higher density in subnets, efficient use of VPNs and AWS Direct Connect.
* Hard limits can be avoided, for example, 50 VIFs per AWS Direct Connect connection through simplified network architecture.
* Costs can be optimized through reuse of NAT gateways, VPC interface endpoints, and intra-Availability Zone traffic

Things to note:

* VPC sharing is only available within the same AWS Organization.
* Sharing of default VPCs/subnets is not possible.
* Participants can’t launch resources using security groups that are owned by other participants or the owner.
* Participants can’t launch resources using the default security group for the VPC because it belongs to the owner.
