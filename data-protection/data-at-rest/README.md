# Data at rest

## Cryptography in AWS&#x20;

Here is a need-to-know primer on what cryptography is mainly used for in AWS.&#x20;

### In transit vs at rest

Encryption in transit refers to TLS/SSL. This is achieved through certificates. The relevant service here is ACM, Amazon Certificate Manager.&#x20;

Encryption at rest is achieved through either client-side or server-side encryption.&#x20;

_Client-side encryption_ is encrypting data at or close to its source, such as encrypting data in the application or service that generates it.

_Server-side encryption_ is encrypting data at its destination, that is, the application or service that receives it.

### Asymmetric vs symmetric encryption&#x20;

Asymmetric or public-key encryption consists of two keys: a public key and a private key. The public key is used to encrypt data and the private key is used to decrypt it. In AWS the asymmetric algorithms are typically RSA and ECC.&#x20;

In symmetric encryption the same key is used for both purposes. In AWS the symmetric algorithm is typically AES with different key lengths.&#x20;

### Envelope encryption&#x20;

Envelope encryption is a strategy for protecting the encryption keys that you use to encrypt your data. First, you encrypt [plaintext](https://docs.aws.amazon.com/crypto/latest/userguide/cryptography-concepts.html#define-plaintext) data with a [data key](https://docs.aws.amazon.com/crypto/latest/userguide/cryptography-concepts.html#define-data-key). Then, to protect the data key, you encrypt it under another key, known as a [key encryption key](https://docs.aws.amazon.com/crypto/latest/userguide/cryptography-concepts.html#define-key-encryption-key).

