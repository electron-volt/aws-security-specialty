# Envelope encryption

KMS keys can only encrypt data up to 4 KB in size. For anything larger that that you need to use envelope encryption.&#x20;

Envelope encryption is the practice of encrypting plaintext data with a data key, and then encrypting the data key under another key.

### Encrypting data

We need to request KMS to generate a data key.&#x20;

KMS returns an object with an encrypted and plain text version of the data key.&#x20;

The plain text data key can be used to encrypt our data.

We should destroy the plain text data key from memory and save the encrypted data key which can be referenced to decrypt the file later.

### Decrypting data

We need to get the plain text data key that was used to encrypt our data.&#x20;

Since our CMK in KMS generated the plain text and encrypted data key pair, it can decrypt the encrypted data key and return the plain text key.&#x20;

The saved encrypted data key can be sent to KMS to be decrypted using our CMK.&#x20;

After the retrieval of the plain text data key we can use it to decrypt the encrypted data.
