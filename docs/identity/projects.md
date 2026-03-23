---
sidebar_label: Users & Projects
---

# Users & Projects

In SovereignSecure Cloud, multi-tenancy and secure resource isolation are achieved through the use of **Projects** (traditionally referred to as Tenants) and **Users**.

## What is a Project?

A **Project** is a logical container used to group and isolate cloud resources. Every resource you create—whether it is a Compute Instance, a Virtual Private Cloud (VPC), a Block Storage volume, or a Kubernetes cluster—belongs to a specific project.

* **Resource Isolation:** Users cannot view or interact with resources outside of the projects they have been explicitly granted access to.
* **Quotas and Limits:** Cloud resource boundaries (e.g., maximum number of vCPUs, total RAM, or allocated storage) are defined at the project level to prevent resource exhaustion.
* **Billing and Showback:** Usage metrics and financial chargebacks are tracked per project, making it easy to allocate costs to different departments, workloads, or teams within your organization.

## What is a User?

A **User** represents a human operator or an automated service account (API user) authenticated centrally via **Keycloak**. 

While a user maintains a single, federated identity across the entire SovereignSecure Cloud platform, their authorization to perform actions is determined strictly by the **Roles** they are assigned within specific **Projects**.

### User-to-Project Mapping

The relationship between users and projects is many-to-many:
* A single user can be a member of multiple projects.
* A single project can have multiple users assigned to it.
* A user can hold different roles in different projects. For example, a user might be an `admin` in the "Development" project, but a read-only `reader` in the "Production" project.

## Managing Project Access

Tenant administrators can manage user access to their projects directly via the Cloud Management Platform (CMP):

1. Navigate to **Identity > Projects** in the CMP.
2. Select your target project.
3. Go to the **Members** tab to view the current list of authorized users.
4. Click **Add Member** to search for an existing organizational user.
5. Select the user and assign them an appropriate Role (e.g., `member`, `reader`, or `admin`).

*(For detailed information on the specific permissions associated with each assignment, please refer to the Roles & Policies documentation).*