# NACL and security group

## NACL&#x20;

Network Access Control List works as a subnet-level firewall. It is stateless, meaning that you need to configure both inbound and outbound rules explicitly.&#x20;

All VPC's come with a default NACL that **allows** all inbound and outbound traffic (IP v4, v6 or both depending on your VPC).&#x20;

If you create your own NACL, it will **deny** all inbound and outbound traffic unless you specifically allow it.&#x20;

Each subnet must be associated with a NACL. Unless you specify your own NACL, the subnet is associated with the default NACL.&#x20;

A subnet can only have one NACL. The same NACL can be used for many subnets.&#x20;

Both inbound and outbound rules can **allow or deny** traffic.&#x20;

## Security group&#x20;

Security groups are an instance-level firewall. It is stateful, meaning that the response to an allowed request is automatically allowed. Security groups deny traffic by default: anything that is not explicitly allowed is denied.&#x20;

You cannot use security groups to block traffic. Rather everything is blocked by default and you allow the traffic you want to let in.

Unless you specify a security group for an instance, it is automatically associated with the VPC's default security group.&#x20;

## Traffic that is not filtered

Amazon security groups and network ACLs do not filter traffic destined to and from the following Amazon services:

* Amazon Domain Name Services (DNS)
* Amazon Dynamic Host Configuration Protocol (DHCP)
* Amazon EC2 instance metadata
* Amazon Windows license activation
* Amazon Time Sync Service
* Reserved IP address of the default VPC router

## Restricting traffic between subnets

In a VPC, all subnets are implicitly associated with the main route table which has a local route to the CIDR of the VPC. If you want to restrict traffic between subnets, you can use either security groups or NACL's.&#x20;

AWS have this to say about it:\
Leverage **security groups** as the primary mechanism for controlling network access to VPCs. When necessary, use network ACLs sparingly to provide stateless, coarse-grain network control. https://docs.aws.amazon.com/vpc/latest/userguide/infrastructure-security.html

Network ACLs act as a firewall for associated subnets, controlling both inbound and outbound traffic at the subnet level. https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html

### Host-based firewall on EC2 for complexity

Host-based firewalls on EC2 instances may be used when complex rules are required to exceed the limits of security groups and network ACLs.&#x20;
