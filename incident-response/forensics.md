# Forensics

## Forensics in AWS&#x20;

### Forensic environment

Automatic provisioning of a secure forensic environment can be achieved using AWS CloudFormation.&#x20;

Example steps to create a reusable AMI for a forensic workstation:

1. Choose a base Amazon Machine Image (AMI) (such as Linux or Microsoft Windows) that can be used as a forensic workstation.
2. Launch an Amazon EC2 instance from that base AMI.
3. Harden the operating system, remove unnecessary software packages, and configure relevant auditing and logging mechanisms.
4. Install your preferred suite of open source or private toolkits, as well as any vendor software and packages that you need.
5. Stop the Amazon EC2 instance and create a new AMI from the stopped instance.
6. Create a weekly or monthly process to update and rebuild the AMI with the latest software patches.

### Forensic processes and orchestration

AWS Step Functions can be used to orchestrate forensic processes with AWS Lambda.&#x20;

## EC2Rescue &#x20;

### For Linux

EC2Rescue for Linux is an easy-to-use, open-source tool that can be run on an Amazon EC2 Linux instance to diagnose and troubleshoot common issues using its library of over 100 modules. A few generalized use cases for EC2Rescue for Linux include&#x20;

* gathering syslog and package manager logs
* collecting resource utilization data
* diagnosing/remediating known problematic kernel parameters and common OpenSSH issues.

### For Windows

EC2Rescue for Windows Server is an easy-to-use tool that you run on an Amazon EC2 Windows Server instance to diagnose and troubleshoot possible problems. It is valuable for collecting log files and troubleshooting issues and also proactively searching for possible areas of concern. It can even examine Amazon EBS root volumes from other instances and collect relevant logs for troubleshooting Windows Server instances using that volume.

EC2Rescue for Windows Server has two different modules: a data collector module that collects data from all different sources, and an analyzer module that parses the data collected against a series of predefined rules to identify issues and provide suggestions.

The EC2Rescue for Windows Server tool only runs on Amazon EC2 instances running Windows Server 2008 R2 and later.

#### CLI

The EC2Rescue for Windows Server tool has two execution modes:

* **/online**—This allows you to take action on the instance that EC2Rescue for Windows Server is installed on, such as collect log files.
* **/offline:\<device\_id>**—This allows you to take action on the offline root volume that is attached to a separate Amazon EC2 Windows instance, on which you have installed EC2Rescue for Windows Server.

Exam tip: you can collect memory dumps from EC2 instances that have become unresponsive using the EC2Rescue CLI with the /offline mode and device ID.
