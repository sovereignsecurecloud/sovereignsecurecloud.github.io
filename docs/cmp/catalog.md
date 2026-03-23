---
sidebar_label: Service Catalogs
sidebar_position: 2
---

# Service Catalogs

The Service Catalog is a core feature of the SovereignSecure Cloud Management Platform (CMP), powered by ManageIQ. It provides a self-service portal where users can browse, order, and manage pre-defined and approved cloud services. This streamlines the provisioning process, ensures compliance, and reduces the need for direct IT intervention.

## What are Service Catalogs?

Service Catalogs present a curated list of IT services that your organization has made available. These services can range from simple virtual machines to complex multi-tier applications or Kubernetes clusters, all packaged with pre-approved configurations and policies.

**Key benefits include:**

*   **Self-Service:** Users can provision resources on demand without waiting for manual approvals or configurations.
*   **Standardization:** Ensures that all deployed resources adhere to organizational standards, security policies, and best practices.
*   **Governance & Compliance:** Integrates with quota management and approval workflows to maintain control over resource consumption and spending.
*   **Reduced Operational Overhead:** Automates repetitive provisioning tasks, freeing up IT staff for more strategic initiatives.

## Browsing the Service Catalog

1.  **Log in** to the SovereignSecure Cloud Console.
2.  From the main dashboard, click on the **"Service Catalog"** tile, or navigate through the menu to **Cloud Management (CMP) > Service Catalogs**.
3.  You will see a list of available service items, often grouped by category (e.g., "Compute," "Databases," "Containers," "Applications").
4.  Click on a service item to view its details, including a description, estimated cost (if applicable), and configuration options.

## Ordering a Service

Once you've found the service you need, the ordering process is straightforward:

1.  **Select the desired service item** from the catalog.
2.  A **provisioning form** will appear, pre-populated with default values where possible.
3.  **Fill in the required fields:**
    *   **Service Name:** A unique, descriptive name for your new service instance.
    *   **Project/Department:** Select the project or department this service will be billed to.
    *   **Configuration Options:** Depending on the service, you might choose VM size (flavor), operating system image, storage capacity, network settings, or application-specific parameters.
    *   **Approval Notes (Optional):** Provide any additional information for the approval team, if an approval workflow is in place.
4.  **Review** your selections and the estimated cost.
5.  Click **"Order"** or **"Submit Request"**.

## Tracking Your Service Request

After submitting an order, you can track its status:

1.  Navigate to **Cloud Management (CMP) > My Services**.
2.  Here, you will see a list of all services you have ordered, along with their current status (e.g., "Pending Approval," "Provisioning," "Active," "Failed").
3.  You can click on a service to view its detailed status, logs, and perform actions like "Stop," "Start," or "Retire" (if permitted).