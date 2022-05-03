# AWS VPNs

## AWS Site-to-site VPN <a href="#concepts" id="concepts"></a>

You can use Site-to-site VPN to create a VPN connection between AWS and your on-premises network.&#x20;

### Concepts <a href="#concepts" id="concepts"></a>

The following are the key concepts for Site-to-Site VPN:

* **VPN connection**: A secure connection between your on-premises equipment and your VPCs.
*   **VPN tunnel**: An encrypted link where data can pass from the customer network to or from AWS.

    **Each VPN connection includes two VPN tunnels** which you can simultaneously use for high availability.
* **Customer gateway**: A _customer gateway_ is a resource that you create in AWS that represents the customer gateway device in your on-premises network. To use Amazon VPC with a Site-to-Site VPN connection, you or your network administrator must also configure the customer gateway device or application in your remote network.
* **Customer gateway device**: A physical device or software application on the on-prem side of the Site-to-Site VPN connection.
* **Virtual private gateway**: A virtual private gateway is the VPN endpoint on the Amazon side of your Site-to-Site VPN connection that can be attached to a single VPC.

An example:

![site to site VPN ](<../../../.gitbook/assets/image (2).png>)

## AWS Client VPN&#x20;

AWS Client VPN enables you to securely access AWS resources and resources in your on-premises network.

The following are the key components for using AWS Client VPN.

* **Client VPN endpoint** — Your Client VPN administrator creates and configures a Client VPN endpoint in AWS. Your administrator controls which networks and resources you can access when you establish a VPN connection.
* **VPN client application** — The software application that you use to connect to the Client VPN endpoint and establish a secure VPN connection.
* **Client VPN endpoint configuration file** — A configuration file that's provided to you by your Client VPN administrator. The file includes information about the Client VPN endpoint and the certificates required to establish a VPN connection. You load this file into your chosen VPN client application.

The client establishes the VPN session from their local computer or mobile device using an OpenVPN-based VPN client application. After they have established the VPN session, they can securely access the resources in the VPC in which the associated subnet is located. They can also access other resources in AWS, an on-premises network, or other clients if the required route and authorization rules have been configured.

An example:

![client VPN](<../../../.gitbook/assets/image (1).png>)
