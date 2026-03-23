---
sidebar_label: Security Groups
---

# Security Groups

In SovereignSecure Cloud, a **Security Group** acts as a stateful, virtual firewall that controls inbound (ingress) and outbound (egress) network traffic for your Compute Instances. 

Powered by our OVN SDN layer, security group rules are distributed and enforced directly at the hypervisor port level, ensuring zero-trust networking and preventing lateral movement even between instances on the same subnet.

## Core Concepts

* **Default Deny (Ingress):** By default, when you create a new security group, it contains no inbound rules. This means all incoming traffic to the instance is blocked until you explicitly allow it.
* **Default Allow (Egress):** By default, new security groups include a rule that allows all outbound traffic, permitting instances to reach the internet or other resources.
* **Stateful:** Security groups are stateful. If you allow an inbound request (e.g., HTTP on port 443), the return traffic for that specific connection is automatically allowed, regardless of your outbound rules.
* **Multiple Groups:** You can assign multiple security groups to a single instance. The resulting permissions are the union of all rules from the assigned groups.

## Anatomy of a Rule

When you create a rule within a security group, you define:

* **Direction:** 
    * `Ingress` (Inbound traffic destined for the instance)
    * `Egress` (Outbound traffic originating from the instance)
* **EtherType:** `IPv4` or `IPv6`.
* **IP Protocol:** `TCP`, `UDP`, or `ICMP`.
* **Port Range:** The specific port or range of ports to open (e.g., `22` for SSH, `80` for HTTP).
* **Remote:** Defines the source (for Ingress) or destination (for Egress) of the traffic. This can be:
    * **CIDR Block:** An IP address range (e.g., `0.0.0.0/0` for the entire internet, or `192.168.1.0/24` for a specific subnet).
    * **Another Security Group:** You can dynamically allow traffic from any instance belonging to another specific security group, which is highly useful for tiered architectures (e.g., allowing your `Database` group to accept traffic only from your `Web Servers` group).

## Best Practices for a Sovereign Cloud

* **Principle of Least Privilege:** Never use `0.0.0.0/0` (allow all) unless absolutely necessary for public-facing web services. Restrict administrative ports like `22` (SSH) or `3389` (RDP) to your specific corporate VPN IP ranges or Teleport gateways.
* **Tiered Architectures:** Use Security Group referencing instead of static IPs. Create separate groups like `frontend-sg`, `backend-sg`, and `db-sg`. Allow `db-sg` to only accept port 3306 from `backend-sg`.

## Managing Security Groups

You can manage security groups via the Cloud Management Platform (CMP):

1. Navigate to **Network > Security Groups**.
2. Click **Create Security Group** and provide a descriptive name (e.g., `web-server-ports`).
3. Select the new group and click **Manage Rules**.
4. Click **Add Rule** to specify the protocol, port, and remote IP range.

To apply the security group to an instance:

* **During Creation:** Select the security group in the Network tab when launching a new instance.
* **Post-Creation:** Navigate to **Compute > Instances**, select your instance, and choose **Edit Security Groups** from the Actions menu.