---
sidebar_label: Roles & Policies
---

# Roles & Policies

SovereignSecure Cloud enforces strict access control through **Role-Based Access Control (RBAC)**. By assigning roles to users within specific projects, you can granularly dictate what actions they are permitted to perform, ensuring adherence to the principle of least privilege.

## Standard Roles

To simplify access management, SovereignSecure Cloud provides a set of pre-defined standard roles. When you add a user to a Project, you must assign them one or more of these roles:

* **Admin:** Grants full administrative access within the scope of the project. Admins can provision, modify, and delete any resource (Compute, Storage, Networking, etc.), as well as manage project memberships and quotas.
* **Member:** The standard operator role. Members can create, manage, and delete resources within the project to conduct their daily operations, but they cannot modify project-level configurations or manage other users' access.
* **Reader:** Grants view-only access. Readers can list and view the details of instances, networks, and storage volumes, but cannot create, modify, or delete any resources. This role is highly recommended for security auditors, compliance officers, or automated monitoring service accounts.

## Policies

Behind the scenes, roles are mapped to specific actions using **Policies**. 

A policy is a set of rules evaluated by the underlying cloud services (e.g., Nova for Compute, Neutron for Networking) every time an API request is made. For example, a policy rule might dictate that the API action `compute:create_instance` is only permitted if the requesting user holds the `admin` or `member` role in the target project.

Because SovereignSecure Cloud prioritizes a secure-by-default posture, default infrastructure policies are strictly locked down to prevent unauthorized lateral access or resource exposure.

## Assigning Roles

Role assignments are strictly scoped at the Project level. A user's role in one project does not grant them any privileges in another project unless explicitly assigned.

To assign or change a user's role:

1. Log in to the Cloud Management Platform (CMP).
2. Navigate to **Identity > Projects**.
3. Select the relevant project and go to the **Members** tab.
4. Click **Add Member** to grant access to a new organizational user, or click the **Edit** icon next to an existing user to modify their current role assignment.

!!! tip "Auditing"
    All role assignments and changes are logged and exportable to the SIEM platform (Wazuh) to satisfy compliance and sovereign auditing requirements.