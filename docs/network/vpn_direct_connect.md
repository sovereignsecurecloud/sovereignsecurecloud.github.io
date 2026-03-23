---
sidebar_label: VPN & Direct Connect
---

# VPN & Direct Connect

Enterprise workloads often demand private, secure connectivity that bypasses the public internet. SovereignSecure Cloud provides secure network gateways to connect your on-premises data centers or branch offices directly to your isolated Virtual Private Clouds (VPCs).

## VPN as a Service (VPNaaS)

Our VPNaaS offering, native to OpenStack Neutron, allows you to establish secure, encrypted **IPsec Site-to-Site VPN** tunnels over the internet.

* **Encrypted Tunnels:** Uses industry-standard encryption protocols (AES-256, IKEv2) to secure data in transit.
* **Seamless Integration:** Instances inside your cloud VPC can communicate with your on-premises servers using their private IP addresses, as if they were on the same local network.
* **Self-Service:** VPNaaS connections can be fully configured and managed directly through the CMP under **Network > VPN**.

## Dedicated Interconnect (Direct Connect)

For organizations requiring the highest level of security, massive bandwidth, and consistent low-latency performance, we offer Dedicated Interconnects.

* **Physical Fiber:** Provision a dedicated physical cross-connect from your corporate network or colocation facility directly into our physical SONiC networking fabric.
* **BGP Routing:** Supports dynamic routing via BGP, automatically sharing routes between your on-premises routers and your cloud VPCs.

*To request a Dedicated Interconnect, please raise a ticket via the Support Portal to coordinate with our data center operations team.*