---
sidebar_label: Bare Metal (BMaaS)
---

# Bare Metal as a Service (BMaaS)

SovereignSecure Cloud offers **Bare Metal as a Service (BMaaS)** powered by **OpenStack Ironic**. BMaaS allows you to provision and manage dedicated physical servers with the same automated, API-driven ease as virtual machines.

## Benefits of Bare Metal

While Virtual Machines are ideal for most workloads, certain use cases require raw hardware:

* **No Hypervisor Overhead:** Achieve 100% of the hardware's compute, memory, and I/O performance without the abstraction tax of a hypervisor.
* **Hardware-Level Isolation:** Perfect for the strictest security and compliance regimes that forbid multi-tenant hardware sharing.
* **Specialized Hardware Needs:** Direct access to specialized hardware features, low-level CPU instruction sets, or specific PCI devices.
* **Nested Virtualization:** Bring your own hypervisor (BYOH). You can run your own virtualization stack (like Proxmox or VMware) directly on top of our bare metal instances.

## How It Works

Through the Cloud Management Platform (CMP) or the OpenStack CLI, you can select a Bare Metal flavor instead of a standard VM flavor. 

1. The **Ironic** service securely wipes the physical disk of the target machine.
2. The server is booted over the network (PXE) and your chosen OS image is flashed directly to the physical drive.
3. The machine is attached to your VPC, operating securely within your private SDN layer.