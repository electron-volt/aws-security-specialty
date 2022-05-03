# Database security

## RDS

### Encryption at rest

The only time that an RDS database can be encrypted is when it is created. If you have created an unencrypted RDS database, the only way you can encrypt it is as follows:

* take a snapshot
* encrypt the snapshot
* use the restore feature to create a new DB from the encrypted snapshot

This will be in principle a different database with different connection strings. You need to update your applications accordingly.&#x20;

#### Read replicas

The read replica of an encrypted DB is encrypted and vice versa. If the DB and RR are in the same region, they use the same encryption keys. If in different regions, they use different keys.&#x20;

### Encryption in transit

RDS database instances are cofingured with an SSL/TLS certificate. You can download the AWS-provided root certificates from AWS for all Regions or specific Regions.

### Access control&#x20;

You can integrate RDS with IAM authentication or use GRANTs in the database itself to allow users access to the various database tables.&#x20;

## DynamoDB

### Encryption at rest

DynamoDB is encrypted at rest by default. The encryption uses AWS-owned keys, which the customer has no access to or control over. This is free of charge.

If your data is very sensitive, you can also use client-side encryption using the DynamoDB Encryption Client.&#x20;

### Encryption in transit

Use TLS.&#x20;

### Access control

Control access to DynamoDB with IAM policies and roles.&#x20;
