# VPC endpoints

We will discuss two types of VPC endpoints: interface endpoint and gateway endpoint.&#x20;

A _gateway endpoint_ is a gateway that you specify in your route table to access Amazon S3 or DynamoDB from your VPC over the AWS network. Other AWS services do not support gateway endpoints at the moment.&#x20;

_Interface endpoints_ extend the functionality of gateway endpoints by using private IP addresses to route requests to services from within your VPC, on premises, or from a VPC in another AWS Region using VPC peering or AWS Transit Gateway.&#x20;

## Interface VPC endpoint

You can create an interface VPC endpoint to connect to services powered by AWS PrivateLink, including many AWS services.

For each subnet that you specify from your VPC, AWS creates an endpoint network interface in the subnet and assigns it a private IP address from the subnet address range. An endpoint network interface is a requester-managed network interface; you can view it in your AWS account, but you can't manage it yourself.

## Gateway endpoint

Gateway endpoints provide reliable connectivity to Amazon S3 and DynamoDB without requiring an internet gateway or a NAT device for your VPC. Gateway endpoints do not enable AWS PrivateLink.

You can access **Amazon S3** and **DynamoDB** through their public service endpoints or through gateway endpoints.&#x20;

#### **Access through an internet gateway**

* Traffic to Amazon S3 or DynamoDB from an instance in a **public** subnet is routed to the internet gateway for the VPC and then to the service. While traffic to Amazon S3 or DynamoDB traverses the internet gateway, it does not leave the AWS network.
* Instances in a **private** subnet can't send traffic to Amazon S3 or DynamoDB, because by definition private subnets do not have routes to an internet gateway. To enable instances in the private subnet to send traffic to Amazon S3 or DynamoDB, you would need to add a NAT device to the public subnet and route traffic in the private subnet to the NAT device.&#x20;

#### Access through a gateway endpoint

Traffic from your VPC to Amazon S3 or DynamoDB is routed to the gateway endpoint. Each subnet route table must have a **route** that sends traffic destined for the service to the gateway endpoint using the prefix list for the service.

All instances in the subnets associated with a route table associated with a gateway endpoint automatically use the gateway endpoint to access the service. Instances in subnets that aren't associated with these route tables use the public service endpoint, not the gateway endpoint.
