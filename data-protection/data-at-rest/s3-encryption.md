# S3 Encryption

S3 offers many different options for encryption. We present them here in order of decreasing operational overhead.&#x20;

## Client-side encryption for S3

Data is encrypted close to the source, on the client side and uploaded to S3 fully encrypted.&#x20;

## SSE-S3

Server-side encryption with S3-managed keys. There are no additional fees to use SSE-S3 (just standard S3 request charges). In most cases this is a good way to do S3 encryption.&#x20;

If you need server-side encryption for all of the objects that are stored in a bucket, use a **bucket** **policy**. For example, use the bucket policy to deny permissions to upload an object unless the request includes the `x-amz-server-side-encryption` header to request server-side encryption (good exam tip).&#x20;

## SSE-KMS

Server-Side Encryption with AWS KMS keys. There are additional charges for using KMS keys. You can cut costs by using bucket-level keys: you don't have a different key for each object, but one key for the bucket. This reduces API calls from S3 to KMS, saving you money.&#x20;

AWS KMS uses _envelope encryption_. Envelope encryption is the practice of encrypting your plaintext data with a data key, and then encrypting that data key with a root key.

## SSE-C

Server-Side Encryption with Customer-Provided Keys. You the customer manage the keys, AWS manages the encryption. There may be some regulation that states that you have to have complete ownership of the cryptographic materials - in that case SSE-C is a good fit.

## Enforcing encryption

1. Add a condition to the S3 bucket policy that allows actions if the request meets the condition "aws:SecureTransport": "true".&#x20;
2. Configure default encryption for the S3 bucket. Add a condition to the S3 bucket policy that denies PUT requests that don’t include the “x-amz-server-side-encryption” header.
