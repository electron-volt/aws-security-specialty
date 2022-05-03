# Route 53

Route 53 is AWS's DNS service that  provides highly available and scalable Domain Name System (DNS), domain name registration, and health-checking web services.

## CNAME versus Alias

Amazon Route 53 offers alias records, which are an _Amazon Route 53-specific_ extension to DNS. You can create alias records to route traffic to selected AWS resources, including Amazon Elastic Load Balancing load balancers, Amazon CloudFront distributions, AWS Elastic Beanstalk environments, API Gateways, VPC interface endpoints, and Amazon S3 buckets that are configured as websites. Alias record typically have a type of A or AAAA, but they work like a CNAME record. Using an alias record, you can map your record name (example.com) to the DNS name for an AWS resource (elb1234.elb.amazonaws.com). Resolvers see the A or AAAA record and the IP address of the AWS resource.

CNAME or canonical name record is similar to Alias, but the key difference is this:&#x20;

* Unlike a CNAME record, **you can create an alias record at the top node of a DNS namespace, also known as the **_**zone apex**_**.**&#x20;

For example, if you register the DNS name example.com, the zone apex is example.com. You can't create a CNAME record for example.com, but you can create an alias record for example.com that routes traffic to www.example.com (as long as www.example.com doesn't already have a CNAME record).

## Routing policies

Here is a quick overview of the different routing policies that Route 53 offers.&#x20;

### Simple routing

If your routing has no special requirements, you can use simple routing. An example is that you have a domain my-site.com and you have it point to one or more IP addresses.&#x20;

### Failover routing

Failover routing is used for active-passive failover. You have two resources, one is active and the other passive. Traffic is routed to the active healthy resource. If it becomes unhealthy, traffic is then routed to the formerly passive resource.&#x20;

### Geolocation routing

Requests are routed to resources based on the geographic location of your users. For example your company serves customers in central Europe and you want to direct French users to the French version of your website and route German users to the German version. You can also use geolocation routing to restrict distribution of content in specific countries. &#x20;

### Geoproximity routing&#x20;

Geoproximity routing lets Amazon Route 53 route traffic to your resources based on the geographic location of your users and your resources. You can also optionally choose to route more traffic or less to a given resource by specifying a value, known as a _bias_. A bias expands or shrinks the size of the geographic region from which traffic is routed to a resource. Using geoproximity requires the use of Route 53 traffic flow. Traffic flow is a service used to simplify the process of creating and maintaining records in large and complex configurations.

### Latency routing

If your application is hosted in multiple AWS Regions, you can improve performance for your users by serving their requests from the AWS Region that provides the lowest latency. The lowest latency is usually achieved by routing requests to the closest geographic region, but not always.&#x20;

### Multivalue answer routing

Multivalue answer routing is almost like a poor man's load balancing. It allows you to return multiple resources such as IP addresses in response to DNS queries and it checks the health of those resources so that all the resources that Route 53 returns are healthy.&#x20;

### Weighted routing

You can associate multiple resources with one domain or subdomain and choose how much traffic is routed to each resource. This is useful for load balancing or testing new versions of software. Imagine you are planning on replacing your app version 1 with version 2. You can direct 80% of traffic to the stable app1.site.com and direct 20% of traffic to the experimental app2.site.com.&#x20;
