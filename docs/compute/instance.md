---
sidebar_label: Overview
sidebar_position: 1
---

# Instances Overview

An **Instance** in SovereignSecure Cloud is a scalable virtual machine (VM) that provides on-demand compute capacity. Each instance is composed of virtual CPUs, memory, and root block storage, allowing you to deploy and run your applications and workloads in a secure and isolated environment.

Our instance service is powered by OpenStack Nova, offering robust and flexible virtual server capabilities that integrate seamlessly with other SovereignSecure Cloud services.

## Key Features

*   **Scalability:** Easily scale your compute resources up or down by changing instance flavors to match your workload demands.
*   **Flexibility:** Choose from a wide range of operating system images, including popular Linux distributions and Windows Server.
*   **Network Integration:** Connect instances to your Virtual Private Clouds (VPCs) and subnets, enabling secure and private network communication.
*   **Security:** Utilize Security Groups to define granular firewall rules, protecting your instances from unauthorized access.
*   **Persistent Storage:** Instances can be provisioned with persistent block storage for their root disk, and additional volumes can be attached for application data.
*   **API & Automation:** Full API support allows for programmatic control and automation of instance provisioning and management.

## Components

Every instance is built using the following core components:

*   **Flavor:** Defines the compute capacity (vCPUs and RAM) allocated to the instance.
    *   Examples: `t1.micro`, `m1.small`, `c1.medium`
*   **Image:** The operating system template (e.g., Ubuntu, RHEL, Windows Server) used as the base for your instance's root disk.
*   **Storage:**
    *   **Root Disk:** The primary Block Storage volume where the operating system is installed.
    *   **Additional Volumes:** Persistent Block Storage volumes that can be attached to instances for application data, providing durability and flexibility.
*   **Network:**
    *   **Virtual Network Interfaces (Ports):** Connect instances to your defined VPC subnets.
    *   **Floating IP:** An optional public IP address that can be associated with an instance for direct internet access.
*   **Security Groups:** Virtual firewalls that control inbound and outbound network traffic to and from your instances.
*   **Key Pair:** Used for secure SSH access to Linux instances.

## Instance Lifecycle

Instances typically follow a lifecycle that includes:

*   **Creation:** Provisioning a new instance from an image and flavor.
*   **Running:** The active state where your applications are operational.
*   **Stopping/Starting:** Temporarily halting or resuming an instance.
*   **Resizing:** Changing the instance's flavor to adjust its compute resources.
*   **Snapshotting:** Creating an image from a running or stopped instance.
*   **Deletion:** Permanently terminating an instance and its associated resources.

## Getting Started

To learn how to create and manage your instances step-by-step, please refer to the Instance User Guide.