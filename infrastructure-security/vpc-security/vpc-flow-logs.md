# VPC Flow Logs

VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC. Flow log data can be published to Amazon CloudWatch Logs or Amazon S3.

Flow Logs capture information about the following:

* Allowed and denied traffic
* Source and destination IP addresses
* Ports
* Protocol number
* Packet and byte counts
* Action taken (accept or reject)

You can use VPC Flow Logs to troubleshoot connectivity and security issues, and to make sure that the network access rules are working as expected.

### Scope

You can create a flow log for a VPC, a subnet, or a network interface.&#x20;

If you create a flow log for a subnet or VPC, each network interface in that subnet or VPC is monitored.

### Example&#x20;

In this example, SSH traffic (destination port 22, TCP protocol) to network interface eni-123 in account ACCOUNT was allowed.

```
2 ACCOUNT eni-123 172.31.16.139 172.31.16.21 20641 22 6 20 4249 1418530010 1418530070 ACCEPT OK
```

In this example, RDP traffic (destination port 3389, TCP protocol) to network interface eni-123 in account ACCOUNT was rejected.

```
2 ACCOUNT eni-123 172.31.9.69 172.31.9.12 49761 3389 6 20 4249 1418530010 1418530070 REJECT OK
```

\
