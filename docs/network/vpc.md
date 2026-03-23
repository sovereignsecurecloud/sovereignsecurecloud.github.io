---
sidebar_label: VPC & Subnets
---

# Virtual Private Cloud (VPC) & Subnets

In SovereignSecure Cloud, a **Virtual Private Cloud (VPC)** is a logically isolated, private network topology dedicated to your project. Powered by our OVN/SONiC SDN stack, it provides complete control over your network environment, including IP address ranges, subnets, and routing.

## Virtual Private Clouds (VPCs)

A VPC acts as the foundational boundary for your cloud resources. By default, resources deployed in a VPC cannot communicate with the outside internet or with other VPCs unless explicitly configured to do so via Routers and Floating IPs.

**Key Characteristics:**
*   **Absolute Isolation:** Each VPC is entirely isolated at Layer 2 and Layer 3, ensuring sovereign boundaries between different tenants and projects.
*   **Custom Topology:** You can define your own internal IP address space (e.g., `10.0.0.0/16` or `192.168.1.0/24`) without worrying about overlapping with other tenants.

## Subnets

A **Subnet** is a segmented portion of a VPC's IP address range where you can place groups of isolated resources. When you launch a Compute Instance, you connect it to one or more specific subnets.

**Subnet Features:**
*   **CIDR Blocks:** You specify the exact Classless Inter-Domain Routing (CIDR) block for each subnet (e.g., `10.0.1.0/24`).
*   **DHCP & DNS:** Each subnet features an integrated, highly available DHCP server to automatically assign IP addresses to your instances. Internal DNS resolution is also provided by default so instances can resolve each other by their hostname.
*   **Gateway IP:** Subnets typically reserve the first usable IP address (e.g., `10.0.1.1`) as the default gateway for routing traffic out of the subnet.

## Creating a VPC and Subnet

You can design your network topology directly through the Cloud Management Platform (CMP):

1. Navigate to **Network > VPCs**.
2. Click **Create VPC**.
3. Provide a name and description for your VPC.
4. Once the VPC is created, click on it and select **Create Subnet**.
5. Define the Subnet Name, Network Address (CIDR), and Gateway IP.
6. (Optional) Configure specific DHCP allocation pools or custom DNS name servers for the subnet.

## Next Steps

Once your isolated network foundation is established, you will likely need to:
*   Create a **Router** to allow traffic to flow between subnets or out to the internet.
*   Attach a **Floating IP** to make an instance publicly accessible.