---
sidebar_label: Routers & Floating IPs
---

# Routers & Floating IPs

While a Virtual Private Cloud (VPC) provides isolated Layer 2 network segments (subnets), you need **Routers** to enable Layer 3 communication between these subnets and the outside world. To expose your resources to the public internet, you use **Floating IPs**.

## Virtual Routers

In SovereignSecure Cloud, a Virtual Router functions similarly to a physical router in a traditional datacenter. Powered by our distributed OVN SDN layer, routing often happens directly at the hypervisor edge, providing highly efficient packet delivery.

### Key Capabilities

* **Subnet Routing:** Connect multiple private subnets within the same VPC, allowing instances in different subnets to communicate with each other.
* **External Gateway (SNAT):** By attaching a router to the External Network (Internet), instances within your private subnets gain outbound internet access (Source NAT). This allows instances to download updates or access external APIs without being directly reachable from the outside.

## Floating IPs (FIPs)

A **Floating IP** is a publicly routable IP address that you can dynamically associate with and disassociate from a Compute Instance or Load Balancer.

### How it Works

* **Static Public Presence:** Instances typically only have private IP addresses (e.g., `10.0.1.5`). A Floating IP provides a static, public-facing IP (e.g., `203.0.113.10`).
* **1-to-1 NAT:** The Virtual Router handles the 1-to-1 Network Address Translation (NAT) between the public Floating IP and the instance's private IP. The instance itself is unaware of its public IP.
* **High Availability:** If an instance fails, you can instantly remap its Floating IP to a standby instance, minimizing downtime for your application's public endpoint.

## Configuration Steps

### 1. Create a Router
1. Navigate to **Network > Routers** in the Cloud Management Platform (CMP).
2. Click **Create Router**, give it a name, and select the **External Network** to enable outbound internet access.
3. Once created, click on the router, navigate to **Interfaces**, and **Add Interface** to connect your internal VPC subnets.

### 2. Allocate and Associate a Floating IP
1. Navigate to **Network > Floating IPs**.
2. Click **Allocate IP to Project** to draw a new public IP from the provider pool.
3. Select the newly allocated IP and click **Associate**.
4. Choose the instance port (private IP) you wish to map the Floating IP to.

!!! tip "Security First"
    Attaching a Floating IP makes your instance publicly reachable. Ensure you have properly configured **Security Groups** to restrict inbound traffic only to necessary ports (e.g., port 443 for HTTPS or port 22 for SSH).