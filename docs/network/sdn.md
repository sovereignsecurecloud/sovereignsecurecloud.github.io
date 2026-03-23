---
sidebar_label: SDN (SONiC & OVN)
---

# Software Defined Networking (SDN)

SovereignSecure Cloud employs a modern Software-Defined Networking (SDN) architecture to ensure scalable, secure, and isolated communications. Our network fabric is built on the powerful combination of **SONiC** and **OVN**.

## Physical Underlay: SONiC

**SONiC (Software for Open Networking in the Cloud)** is an open-source network operating system based on Linux that runs on switches from multiple vendors. 

* **Vendor Agnostic:** Frees the infrastructure from proprietary networking hardware limitations.
* **High Performance:** Provides the robust, high-speed physical routing (Layer 3) underlay required for massive cloud scale.

## Virtual Overlay: OVN (Open Virtual Network)

**OVN** serves as the control plane for our virtual networks, natively integrating with OpenStack Neutron.

* **Virtual Private Clouds (VPC):** OVN creates isolated Layer 2 and Layer 3 topologies for tenants over the physical SONiC underlay using GENEVE tunneling.
* **Distributed Routing:** Routing between subnets happens at the hypervisor level, reducing network bottlenecks and tromboning.
* **Distributed Security Groups:** Firewall rules are implemented at the virtual port level (OVS), ensuring zero-trust networking between instances even within the same subnet.