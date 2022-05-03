# AWS CloudFront

AWS CloudFront is AWS's content distribution service. We assume the reader is familiar with origins, distributions, caching and edge locations.&#x20;

## Securing CloudFront&#x20;

You can secure your CloudFront distribution in many ways;

* Use AWS WAF in front of the distribution&#x20;
* Use signed cookies or signed URL's
* For S3 origins, use an Origin Access Identity or OAI to prevent users from accessing the origin directly
* Use field-level encryption to ensure end-to-end encryption&#x20;
* Restrict access from certain geolocations
* For encryption in transit use HTTPS.&#x20;

## HTTPS and CloudFront

### Viewer HTTPS configuration

CloudFront comes with native HTTPS support. You can configure CloudFront to deliver contents via HTTPS from viewer to origin, end to end.

In CloudFront, the HTTPS setting is configurable for two different connections:

* Viewer to CloudFront
* CloudFront to origin.

Because the HTTPS is initiated by the client, CloudFront has options to:

* Accept both HTTP and HTTPS
* Let the client use HTTPS if they initiate the request via HTTP, or
* Ignore HTTP and respond with an error message

These options can be applied to a specific URI path so you can configure some part of your website to accept HTTP.

### Origin HTTPS configuration&#x20;

When connecting to the origin with HTTPS, CloudFront becomes a client who initiates a TLS handshake. In this context, CloudFront operation is focused on authenticating the origin to avoid possible man-in-the-middle attacks. CloudFront trusts only the origin server when the TLS certificate provided by the origin server meets the following conditions:&#x20;

* The certificate matches the requested domain name
* The certificate is issued by a trusted certificate authority (CA)
* The certificate chain is correct
* The certificate is not expired

If any of these conditions are not met, CloudFront drops the connection to the origin and responds with an error message to the client.

## Signed cookies and URL's

Use signed URLs in the following cases:

* You want to restrict access to **individual** files, for example, an installation download for your application.
* Your users are using a client (for example, a custom HTTP client) that doesn't support cookies.

Use signed cookies in the following cases:

* You want to provide access to **multiple** restricted files, for example, all of the files for a video in HLS format or all of the files in the subscribers' area of website.
* You don't want to change your current URLs.

Note: Signed URLs take precedence over signed cookies. If you use both signed URLs and signed cookies to control access to the same files and a viewer uses a signed URL to request a file, CloudFront determines whether to return the file to the viewer _based only on the signed URL._

### Using a signer

To create signed URLs or signed cookies, you need a _signer_. A signer is either a trusted key group that you create in CloudFront, or an AWS account that contains a CloudFront key pair. AWS recommend that you use trusted key groups with signed URLs and signed cookies, because:

* if you use key pairs, you need to use the root account to manage them&#x20;
* with key groups you can use the API to manage keys and automate tasks. With root, you must use the console and there is no automation&#x20;
* with key groups you can use IAM policies to restrict permissions. With root there are no restrictions.&#x20;
* with root you are limited to two active key pairs per account. With trusted key groups you have more flexibility with keys.&#x20;

## Origin Access Identity&#x20;

To restrict access to content that you serve from Amazon S3 buckets, follow these steps:

1. Create a special CloudFront user called an origin access identity (OAI) and associate it with your distribution. This is done in the CloudFront console or API, not IAM!&#x20;
2. Configure your S3 bucket permissions so that CloudFront can use the OAI to access the files in your bucket and serve them to your users. Make sure that users can’t use a direct URL to the S3 bucket to access a file there.

After you take these steps, users can only access your files through CloudFront, not directly from the S3 bucket. For maximum security, use OAI's in conjunction with signed cookies or URL's.&#x20;

If your S3 bucket is a website endpoint, you have to configure it as a custom origin. In that case you cannot use OAI, but have to use custom headers instead.&#x20;

## Georestriction

When a user requests your content, CloudFront typically serves the requested content regardless of where the user is located. If you need to prevent users in specific countries from accessing your content, you can use the CloudFront geographic restrictions feature to do one of the following:

* Allow your users to access your content only if they’re in one of the approved countries on your allow list.
* Prevent your users from accessing your content if they’re in one of the banned countries on your block list.

Another alternative is to use a 3rd party. This can allow you to control access to your content based not only on country but also based on city, zip or postal code, or even latitude and longitude. AWS recommend you use this in conjunction with signed URL's.

## Field-level encryption

You can enforce secure end-to-end connections to origin servers by using HTTPS. Along the route from origin to requester there can be services that decrypt and encrypt the data, so you can in addition to HTTPS use field-level encryption as an additional security mechanism.&#x20;

