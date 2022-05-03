# NAT devices

## NAT Gateway&#x20;

Allow internet access to instances in private subnets with a NAT gateway. It will not allow unsolicited requests from the internet, but will allow the instances in the private subnet internet access, for example to fetch updates. The NAT gateway itself must be in a public subnet. Configure a route to the NAT gateway in the route table of the private subnet.&#x20;

### NAT instance

NAT gateways have many advantages but they are expensive. In some use cases it might be sufficient to have a NAT instance, which is an EC2 instance that you spin up and use as a NAT device.&#x20;

#### Source/destination checks &#x20;

Each EC2 instance performs source/destination checks by default. This means that the instance must be the source or destination of any traffic it sends or receives. However, an inline security appliance must be able to send and receive traffic when the source or destination is not itself. Therefore, you must disable source/destination checks on these instances.&#x20;

A NAT instance can become a performance bottleneck and they have no in-built high availability, so you must implement it yourself if you need it.&#x20;

## IPv6 egress-only IGW&#x20;

IPv6 has no such thing as private IP's, so NAT is not needed. For IPv6 you can use an egress-only IGW, which works much like a NAT gateway does for IPv4.&#x20;

An egress-only internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows outbound communication over IPv6 from instances in your VPC to the internet, and prevents the internet from initiating an IPv6 connection with your instances.

