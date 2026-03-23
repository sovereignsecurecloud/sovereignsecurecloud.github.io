---
sidebar_label: Overview
sidebar_position: 1
---

# Networking Overview

Welcome to the SovereignSecure Cloud Networking documentation. Our networking services provide the foundational connectivity, isolation, and security required to build robust and compliant cloud architectures.

Powered by a modern Software-Defined Networking (SDN) stack utilizing SONiC and OVN, integrated natively with OpenStack Neutron, we offer a highly scalable and secure network fabric.

## Core Networking Services

Explore the following sections to learn how to architect and manage your network resources:

* **[SDN Architecture](sdn.md):** Understand the underlying Software-Defined Networking technologies (SONiC & OVN) that power our secure and scalable fabric.
* **[VPC & Subnets](vpc.md):** Learn how to create isolated Virtual Private Clouds (VPCs) and partition them into Subnets to organize your resources.
* **[Routers & Floating IPs](routers_fips.md):** Discover how to route traffic between your internal subnets and manage external access using Floating IPs.
* **[Security Groups](security_group.md):** Implement zero-trust security by configuring stateful, distributed firewall rules at the instance level.
* **[Load Balancers](load_balancer.md):** Distribute incoming traffic across multiple instances to ensure high availability and application resilience.

## Network Isolation & Sovereignty

By default, all tenant VPCs are strictly isolated from one another at Layer 2 and Layer 3. You maintain complete control over ingress and egress traffic, ensuring your network architecture aligns perfectly with strict data sovereignty and security compliance frameworks.