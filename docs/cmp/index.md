
---
sidebar_label: Overview
sidebar_position: 1
---

# Cloud Management Platform (CMP)

Welcome to the SovereignSecure Cloud Management Platform (CMP) documentation. Powered by ManageIQ, our CMP provides a unified, self-service portal for managing your multi-tenant, sovereign cloud environment. 
It empowers users to orchestrate workloads, track utilization, and govern project resources with ease, all while adhering to strict data sovereignty principles.

## Benefits of SovereignSecure CMP

Leveraging our CMP offers several key advantages for your organization:

*   **Enhanced Governance:** Centralized control over resource provisioning, ensuring compliance with organizational policies and regulatory requirements.
*   **Cost Transparency:** Detailed chargeback and showback reporting to accurately track and attribute cloud spending.
*   **Self-Service Provisioning:** Empower users to quickly deploy approved services from a curated catalog, reducing operational overhead.
*   **Operational Efficiency:** Automate routine tasks and lifecycle management for virtual machines, containers, and other cloud resources.
*   **Multi-Cloud Readiness:** While currently focused on OpenStack, ManageIQ provides a foundation for future multi-cloud management capabilities.

## Key Capabilities

* **[Service Catalogs](catalog.md):** A self-service portal where users can order predefined, approved IT services, such as standard Virtual Machines, multi-tier application stacks, and Kubernetes clusters.
* **[Chargeback & Reporting](reporting.md):** Track the financial cost of running your workloads. Generate detailed showback/chargeback reports based on CPU, memory, storage, and network utilization.
*   **Lifecycle Management:** Automate the provisioning, retirement, and scaling of instances and other cloud resources, streamlining operations and ensuring resource optimization.
*   **Quota & Policy Enforcement:** Define and enforce resource quotas and operational policies across projects and users, maintaining control and preventing resource sprawl.

## Accessing the Cloud Console

1.  **Open your web browser** and navigate to the SovereignSecure Cloud Console URL: `https://portal.sovereignsecurecloud.com`
2. Log in using your organizational Single Sign-On (SSO) credentials or your project-specific administrator account.
3. From the dashboard, you can view a summary of your running workloads, pending catalog requests, and recent alerts.

## Additional Cloud Supported

1. Alibaba Cloud
2. Huawei Cloud
3. Amazon Web Services (AWS)
4. Microsoft Azure
5. Google Cloud Platform (GCP)
6. Oracle Cloud
7. Tencent Cloud
8. OpenStack Cloud
9. VMware vSphere
10. Nutanix

!!! tip "For Advanced Users and Automation"
    Beyond the graphical Cloud Console, you can also interact with the CMP and underlying OpenStack infrastructure programmatically. Refer to the API & Automation section for details on using the ManageIQ REST API and OpenStack native CLIs.