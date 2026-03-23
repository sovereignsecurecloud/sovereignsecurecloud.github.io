---
sidebar_label: GPU Instances
sidebar_position: 3
---

# GPU Instances

SovereignSecure Cloud offers specialized Virtual Machine instances equipped with GPUs. These instances are highly recommended for compute-intensive workloads such as Machine Learning, AI training, 3D rendering, and high-performance computing (HPC).

## Create GPU Instances

You can create GPU instances either directly through the Cloud Console or by using Infrastructure as Code (IaC) tools like Terraform and OpenTofu. 

### Choosing a GPU Flavor

When provisioning a GPU instance, you must select a flavor that guarantees hardware acceleration. In our environment, GPU flavors are typically denoted by the `g` prefix.

| Flavor Series | Use Case |
| ----------- | ----------- |
| **g-series** | General-purpose GPU workloads, machine learning, and video processing. |

### Image Considerations

To fully utilize the GPU hardware, the operating system must have the correct NVIDIA grid or passthrough drivers installed. 

* We recommend choosing one of the pre-configured **GPU-enabled Public Images** provided by SovereignSecure Cloud, which come with the necessary drivers and CUDA toolkits pre-installed.
* If you bring your own image, you will be responsible for installing the appropriate drivers via a User Script (cloud-init) during launch.

### OS Settings

Just like standard instances, you must determine how the root block storage is created:

* **Create New and Set up:** Create a fresh root block storage volume using a selected Image. Ensure the disk size meets the minimum requirements for GPU driver installations (typically 40GB+ is recommended).
* **Use Existing Resource:** Boot from a previously created block storage volume or snapshot that already contains your GPU environment setup.

### GPU Instance Lifecycle & Billing

GPU resources are in high demand and are strictly allocated at the hypervisor level using PCI passthrough or vGPU profiles. Please be aware of the following operational limits:

!!! warning "Billing Note"
    Because hardware is heavily reserved, **GPU Instances will incur normal (100%) rates even when stopped**. To completely stop billing for a GPU instance, you must **Terminate (Delete)** the instance. 

!!! note "Live Migration"
    Due to the hardware binding of PCI devices, GPU instances **cannot** be live-migrated between hypervisors. Maintenance events on the underlying host will require the instance to be completely shut down and started on a new host.