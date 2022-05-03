# AWS WAF

AWS WAF is Amazon's web application firewall that can help you protect your AWS resources against common layer 7 web attacks such as cross-site scripting and SQL injection.&#x20;

### How does WAF work

You use AWS WAF to control how an Amazon CloudFront distribution, an Amazon API Gateway REST API, an Application Load Balancer, or an AWS AppSync GraphQL API responds to HTTP(S) web requests.

* **Web ACLs** – You use a web access control list (ACL) to protect a set of AWS resources. You create a web ACL and define its protection strategy by adding rules. Rules define criteria for inspecting web requests and specify how to handle requests that match the criteria. You set a default action for the web ACL that indicates whether to block or allow through those requests that pass the rules inspections.
* **Rules** – Each rule contains a statement that defines the inspection criteria, and an action to take if a web request meets the criteria. When a web request meets the criteria, that's a match. You can configure rules to block matching requests, allow them through, count them, or run CAPTCHA controls against them.
* **Rules groups** – You can use rules individually or in reusable rule groups. AWS Managed Rules and AWS Marketplace sellers provide managed rule groups for your use. You can also define your own rule groups.

After you create your web ACL, you can associate it with one or more AWS resources. The resource types that you can protect using AWS WAF web ACLs are

* an Amazon CloudFront distribution
* an Amazon API Gateway REST API
* an Application Load Balancer
* an AWS AppSync GraphQL API.

### Functionality

At the simplest level, AWS WAF lets you choose one of the following behaviors:

* **Allow all requests except the ones that you specify** – This is useful when you want Amazon CloudFront, Amazon API Gateway, Application Load Balancer, or AWS AppSync to serve content for a public website, but you also want to block requests from attackers.
* **Block all requests except the ones that you specify** – This is useful when you want to serve content for a restricted website whose users are readily identifiable by properties in web requests, such as the IP addresses that they use to browse to the website.
* **Count requests that match your criteria** – You can use the count action to track your web traffic without modifying how you handle it. You can use this for general monitoring and also to test your new web request handling rules. When you want to allow or block requests based on new properties in the web requests, you can first configure AWS WAF to count the requests that match those properties. This lets you confirm your new configuration settings before you implement new allow or block actions.
* **Run CAPTCHA checks against requests that match your criteria** – You can implement CAPTCHA controls against requests to help reduce bot traffic to your protected resources.

### Benefits

Using AWS WAF has several benefits:

* Additional protection against web attacks using conditions that you specify. You can define conditions by using characteristics of web requests such as the following:
  * IP addresses that requests originate from.
  * Country that requests originate from.
  * Values in request headers.
  * Strings that appear in requests, either specific strings or strings that match regular expression (regex) patterns.
  * Length of requests.
  * Presence of SQL code that is likely to be malicious (known as _SQL injection_).
  * Presence of a script that is likely to be malicious (known as _cross-site scripting_).
* Rules that can allow, block, or count web requests that meet the specified conditions. Alternatively, rules can block or count web requests that not only meet the specified conditions, but also exceed a specified number of requests in any 5-minute period.
* Rules that you can reuse for multiple web applications.
* Managed rule groups from AWS and AWS Marketplace sellers.
* Real-time metrics and sampled web requests.
* Automated administration using the AWS WAF API.

### AWS Firewall Manager <a href="#fms-intro" id="fms-intro"></a>

AWS Firewall Manager simplifies your administration and maintenance tasks across multiple accounts and resources for a variety of protections, including AWS WAF, AWS Shield Advanced, Amazon VPC security groups, AWS Network Firewall, and Amazon Route 53 Resolver DNS Firewall. With Firewall Manager, you set up your protections just once and the service automatically applies them across your accounts and resources, even as you add new accounts and resources.
