# Traffic mirroring

Traffic Mirroring is an Amazon VPC feature that you can use to copy network traffic from the elastic network interface of an Amazon EC2 instance. You can then send the traffic to out-of-band security and monitoring appliances for:

* Content inspection
* Threat monitoring
* Troubleshooting

### Benefits

Traffic Mirroring offers the following benefits:

* **Simplified operation** — Mirror any range of your VPC traffic without having to manage packet forwarding agents on your EC2 instances.
* **Enhanced security** — Capture packets at the elastic network interface, which cannot be disabled or tampered with from a user space.
* **Increased monitoring options** — Send your mirrored traffic to any security device.

### Common use cases

* Mirror all inbound TCP traffic to a single EC2 instance
* Mirror all inbound TCP and UDP traffic to a single instance. Send monitored traffic to different devices based on protocol
* Monitor traffic leaving your VPC or traffic whose source is outside your VPC.

## Traffic mirroring and Flow Logs

Compared to Flow logs, Traffic Mirroring provides deeper insight into the network traffic by allowing you to analyze actual traffic content, including payload. Traffic Mirroring is targeted for the following types of cases:

* Analyzing the actual packets to perform a root-cause analysis on a performance issue
* Reverse-engineering a sophisticated network attack
* Detecting and stopping insider abuse or compromised workloads
