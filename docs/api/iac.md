---
sidebar_label: Infrastructure as Code (IaC)
sidebar_position: 3
---

# Infrastructure as Code (IaC)

SovereignSecure Cloud natively supports Infrastructure as Code (IaC) workflows, allowing you to manage and provision your cloud resources using machine-readable definition files. This approach ensures consistency, repeatability, and version control for your infrastructure.

Our platform is fully compatible with popular IaC tools like **Terraform** and **OpenTofu** through the standard OpenStack provider.

## Prerequisites

1.  **Install Terraform or OpenTofu:** Download and install the CLI tool for your operating system.
2.  **Authentication Details:** Ensure you have your `clouds.yaml` file configured, or have sourced your `openrc.sh` file as described in the CLI Configuration guide.

## Configuring the Provider

To begin managing SovereignSecure Cloud resources, you need to configure the OpenStack provider in your configuration files (e.g., `main.tf`).

```hcl
terraform {
  required_version = ">= 1.0.0"
  required_providers {
    openstack = {
      source  = "terraform-provider-openstack/openstack"
      version = "~> 1.50.0"
    }
  }
}

# If you are using clouds.yaml, specify the cloud name:
provider "openstack" {
  cloud = "openstack"
}
```

## Example: Provisioning an Instance

Here is a basic example of provisioning a compute instance using Terraform/OpenTofu:

```hcl
resource "openstack_compute_instance_v2" "my_instance" {
  name            = "terraform-instance"
  image_name      = "Ubuntu 22.04 LTS"
  flavor_name     = "t1.micro"
  key_pair        = "my-ssh-key"
  security_groups = ["default"]
  
  network {
    name = "my-internal-network"
  }
}
```