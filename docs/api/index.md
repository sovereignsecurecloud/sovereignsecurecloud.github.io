---
sidebar_label: Overview
sidebar_position: 1
---

# API Overview

SovereignSecure Cloud provides comprehensive API access, allowing developers and system administrators to automate infrastructure provisioning, configuration, and management. 

Our environment leverages two primary layers of APIs depending on your automation needs:

1. **SovereignSecure Cloud Management Platform (CMP) API**
2. **OpenStack Native Infrastructure APIs**

## Cloud Management Platform (CMP) API

The CMP API is based on ManageIQ and is the recommended entry point for users looking to manage their cloud lifecycle, provisioning requests, quotas, and organizational reporting. It provides a RESTful interface to the unified management tool.

- **Endpoint:** `https://portal.sovereignsecurecloud.com/api`
- **Authentication:** Basic Auth or Token-based authentication
- **Best For:** Self-service provisioning, service catalogs, chargeback/showback data, and multi-tenant organizational management.

## OpenStack Native APIs

For deep infrastructure automation, SovereignSecure Cloud exposes standard OpenStack native APIs. This allows you to use familiar tooling like Terraform, OpenTofu, Ansible, and the standard OpenStack CLI.

- **Identity (Keystone):** Authentication and catalog discovery.
- **Compute (Nova):** Instance lifecycle management.
- **Networking (Neutron):** VPCs, Subnets, Routers, and Floating IPs.
- **Block Storage (Cinder):** Volumes and Snapshots.
- **Image Service (Glance):** OS Images and custom snapshots.
