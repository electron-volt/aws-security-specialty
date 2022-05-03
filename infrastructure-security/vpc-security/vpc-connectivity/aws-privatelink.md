# AWS PrivateLink

AWS PrivateLink is a highly available, scalable technology that enables you to **privately connect your VPC to services** as if they were in your VPC.

You do not need to use an internet gateway, NAT device, AWS Direct Connect connection, or AWS Site-to-Site VPN connection to communicate with the service.

To use AWS PrivateLink, create a **VPC endpoint** in your VPC, specifying the name of the service and a subnet. This creates an elastic network interface in the subnet that serves as an entry point for traffic destined to the service.

## Terminology&#x20;

### Service provider

The owner of a service is the _service provider_. Service providers include AWS, AWS Partners, and other AWS accounts. Service providers can host their services using AWS resources, such as EC2 instances, or using on-premises servers.

### Endpoint services

A service provider creates an _endpoint service_ to make their service available in a Region. A service provider **must specify a load balancer** when creating an endpoint service. The load balancer receives requests from service consumers and routes them to your service.

By default, your endpoint service is **not available** to service consumers. You must add permissions that allow specific AWS principals (AWS accounts, IAM users, and IAM roles) to connect to your endpoint service.

### Service names

Each endpoint service is identified by a service name. A service consumer must specify the name of the service when creating a VPC endpoint. Service consumers can query the service names for AWS services. Service providers must share the names of their services with service consumers.

### Service states <a href="#concepts-service-states" id="concepts-service-states"></a>

The following are the possible states for an endpoint service:

* `Pending` - The endpoint service is being created.
* `Available` - The endpoint service is available.
* `Failed` - The endpoint service could not be created.
* `Deleting` - The service provider deleted the endpoint service and deletion is in progress.
* `Deleted` - The endpoint service is deleted.

### Service consumers <a href="#concepts-service-consumers" id="concepts-service-consumers"></a>

The user of a service is a _service consumer_. Service consumers can access endpoint services from AWS resources, such as EC2 instances, or from on-premises servers.

### VPC endpoints <a href="#concepts-vpc-endpoints" id="concepts-vpc-endpoints"></a>

A service consumer creates a _VPC endpoint_ to connect their VPC to an endpoint service. A service consumer must specify the service name of the endpoint service when creating a VPC endpoint. There are multiple types of VPC endpoints. You must create the type of VPC endpoint that's required by the endpoint service.

* `Interface` - Create an _interface endpoint_ to send traffic to endpoint services that use a Network Load Balancer to distribute traffic. Traffic destined for the endpoint service is resolved using DNS.
* `GatewayLoadBalancer` - Create a _Gateway Load Balancer endpoint_ to send traffic to a fleet of virtual appliances using private IP addresses. You route traffic from your VPC to the Gateway Load Balancer endpoint using route tables. (Unlikely to show up on the exam)
* `Gateway` - Create a _gateway endpoint_ to send traffic to Amazon S3 or DynamoDB using private IP addresses. You route traffic from your VPC to the gateway endpoint using route tables. Gateway endpoints do not enable AWS PrivateLink.

Read more about VPC endpoints on the next page.&#x20;

#### Example: KMS

KMS is AWS's key management service where you can store encryption keys. To connect directly to AWS KMS from your virtual private cloud (VPC) without sending traffic over the public internet, use VPC endpoints, powered by AWS PrivateLink.&#x20;
