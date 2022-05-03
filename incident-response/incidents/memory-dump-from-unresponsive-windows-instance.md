# Memory dump from unresponsive Windows instance

The EC2Rescue for Windows Server command line interface (CLI) allows you to run an EC2Rescue for Windows Server plugin (referred as an “action”) programmatically.

The EC2Rescue for Windows Server tool has two execution modes:

* **/online**—This allows you to take action on the instance that EC2Rescue for Windows Server is installed on, such as collect log files.
* **/offline:\<device\_id>**—This allows you to take action on the offline root volume that is attached to a separate Amazon EC2 Windows instance, on which you have installed EC2Rescue for Windows Server.
