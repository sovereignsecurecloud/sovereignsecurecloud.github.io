---
sidebar_label: SLAs
sidebar_position: 2
---

# Service Level Agreements (SLAs)

SovereignSecure Cloud guarantees enterprise-grade availability and performance to ensure your sovereign workloads are always accessible.

## Availability Targets

We provide financially backed SLAs across our core services:

* **Compute & Virtualization:** 99.99% uptime for hypervisor and instance availability.
* **Block & Object Storage:** 99.99% data availability and 99.9999999% data durability.
* **Network Fabric:** 99.99% availability for core routing and internet/VPC transit.

## Maintenance Windows

To maintain a secure and robust environment, regular maintenance and security patching are performed on the underlying infrastructure. 
* **Non-Disruptive:** Most infrastructure updates (such as live-migrating VMs or rolling Ceph updates) are performed transparently without tenant downtime.
* **Scheduled Maintenance:** For disruptive maintenance (such as underlying network fabric updates or physical host reboots for non-migratable GPU instances), tenants are notified at least **14 days in advance** via the CMP and email.