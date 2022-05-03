# VPC security

## VPC security at a glance

* Stateful and stateless firewalls - security groups and firewalls
* Flow Logs - monitor IP traffic going in and out of network interfaces in your VPC
* Traffic mirroring - capture and monitor traffic in and out of EC2 elastic network interfaces
* VPC endpoints - private connectivity to services inside your VPC
* VPC connectivity options - expand your corporate network into AWS or connect VPC's within AWS&#x20;
* NAT devices - overview of NAT for IPv4 and egress only IGW for IPv6.

### AWS global infrastructure and encryption in transit

All data flowing across AWS Regions over the AWS global network is automatically encrypted at the physical layer before it leaves AWS secured facilities.&#x20;

All traffic between AZs is encrypted.&#x20;

All traffic within a VPC and inter-region peering is transparently encrypted when using supported instance types.&#x20;
