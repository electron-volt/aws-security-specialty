# Edge functions

## Lambda@Edge and CloudFront Functions&#x20;

The code that you write and attach to your CloudFront distribution is called an _edge function_. CloudFront provides two ways to write and manage edge functions:

* **CloudFront Functions** – With CloudFront Functions, you can write lightweight functions in JavaScript for high-scale, latency-sensitive CDN customizations. The CloudFront Functions runtime environment offers submillisecond startup times, scales immediately to handle millions of requests per second, and is highly secure. CloudFront Functions is a native feature of CloudFront, which means you can build, test, and deploy your code entirely within CloudFront.
* **Lambda@Edge** – Lambda@Edge is an extension of [AWS Lambda](http://aws.amazon.com/lambda/) that offers powerful and flexible computing for complex functions and full application logic closer to your viewers, and is highly secure. Lambda@Edge functions run in a Node.js or Python runtime environment. You publish them to a single AWS Region, but when you associate the function with a CloudFront distribution, Lambda@Edge automatically replicates your code around the world.

Which one to use?&#x20;

### CloudFront Functions:&#x20;

* lightweight, short-running functions (function duration can be submillisecond)&#x20;
* only language is JavaScript
* event sources are viewer request and response only
* massive scale: 10 MILLION requests per second or more&#x20;
* quick tasks like header manipulation, URL redirect or rewrite

### Lambda@Edge:

* functions that take several milliseconds or more to complete
* need adjustable CPU or memory&#x20;
* written in Python or NodeJS
* depend on 3rd party libraries
* need network access&#x20;
* need file system access or access to HTTP request body&#x20;
* event sources are viewer request, viewer response, origin request and origin response.&#x20;
