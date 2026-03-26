# Platform Architecture

![Image title](assets/az.png){ width="400" }

OSISM is a comprehensive platform for managing software-defined cloud infrastructure. To build a cloud pod, a specific set of hardware components is required. This Bill of Materials (BOM) provides an overview of the typical hardware components used in an OSISM-managed environment.

---

## 1. Node Role Overview

A standard OSISM deployment consists of several types of nodes, each serving a specific purpose within the infrastructure:

* **Manager Nodes:** Run the OSISM management services (Ansible, Docker registry, netbox, etc.).
* **Control Nodes:** Run the control plane services (OpenStack APIs, databases, message queues).
* **Compute Nodes:** Host the virtual machines (OpenStack Nova).
* **Storage Nodes:** Provide the distributed storage backend (Ceph OSDs).
* **Network Nodes:** Handle external network traffic and L3 services (OpenStack Neutron).

---

## 2. Component Specifications

### Network Switches
The network infrastructure typically relies on high-performance switches supporting modern protocols:

* **Management Switch:** 1 GbE or 10 GbE for out-of-band management (IPMI/BMC).
* **Data/Leaf Switches:** 25 GbE or 100 GbE switches (e.g., Celestica, Edgecore, or Dell) running **SONiC** or other open network operating systems.

### Generic Node Requirements
While specifications vary by role, standard enterprise-grade servers are generally used:

| Component | Specification |
| :--- | :--- |
| **Processor** | Multi-core x86_64 CPUs (AMD EPYC or Intel Xeon) |
| **Memory** | High-density DDR4/DDR5 ECC RAM |
| **Storage** | NVMe or SSD for the operating system and local caching |
| **NICs** | 25 GbE or 100 GbE dual-port adapters (e.g., NVIDIA/Mellanox ConnectX) |

---

## 3. Specific Role Configurations

### Control Nodes
* **CPU:** 16+ Cores.
* **RAM:** 128 GB - 256 GB.
* **Disk:** RAID 1 NVMe for system/databases.

### Compute Nodes
* **CPU:** High core count for VM density.
* **RAM:** 256 GB - 1 TB+ depending on workload requirements.
* **NIC:** Dual-port 25/100 GbE.

### Storage Nodes (Ceph)
* **CPU:** 8-16 Cores.
* **RAM:** 64 GB - 128 GB (Rule of thumb: ~1 GB RAM per 1 TB of OSD storage).
* **Disk:** 4-12+ NVMe or SAS/SATA SSDs for data; dedicated NVMe for WAL/DB.

---

## 4. Software Stack Summary

| Layer | Recommended Component |
| :--- | :--- |
| **Operating System** | Ubuntu 24.04 LTS |
| **IaaS** | OpenStack |
| **SDS (Storage)** | Ceph |
| **SDN (Network)** | SONiC & OVN |
| **Kubernetes** | K3s |
| **Identity Management** | Keycloak |

---