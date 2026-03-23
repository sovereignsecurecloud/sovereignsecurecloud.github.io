---
sidebar_label: Load Balancers
---

# Load Balancers

In SovereignSecure Cloud, Load Balancers as a Service (LBaaS) distribute incoming application traffic across multiple Compute Instances. This increases the availability, fault tolerance, and scalability of your applications. Our load balancing service is natively integrated with the underlying SDN and is powered by OpenStack Octavia.

## Core Components

To set up a load balancer, you configure several interconnected components:

*   **Load Balancer:** The root object that occupies a specific IP address on your subnet. To make it accessible from the internet, you can associate a Floating IP with it.
*   **Listener:** A process that checks for connection requests on a configured protocol and port (e.g., HTTP on port 80, or TCP on port 443).
*   **Pool:** A logical group of backend Compute Instances (Members) that serve the requests routed by the Listener.
*   **Member:** An individual Compute Instance (specified by its private IP and port) belonging to a Pool.
*   **Health Monitor:** A service that periodically pings the Pool Members to ensure they are healthy. If a Member fails a health check, the load balancer stops routing traffic to it until it recovers.

## Key Features

*   **Layer 4 and Layer 7 Load Balancing:** Route traffic based on low-level TCP/UDP protocols (Layer 4) or application-level HTTP/HTTPS headers (Layer 7).
*   **TLS Offloading/Termination:** Centralize SSL/TLS certificates on the load balancer itself, relieving your backend instances from the CPU-intensive task of encrypting and decrypting traffic.
*   **Advanced Routing Algorithms:** Choose how traffic is distributed among your instances:
    *   *Round Robin:* Distributes requests evenly across all members sequentially.
    *   *Least Connections:* Sends new requests to the member with the fewest active connections.
    *   *Source IP:* Routes requests from the same client IP to the same backend member (Session Persistence).

## Creating a Load Balancer

You can provision and configure Load Balancers via the Cloud Management Platform (CMP):

1.  Navigate to **Network > Load Balancers**.
2.  Click **Create Load Balancer**.
3.  **Basic Details:** Provide a name, select the target VPC/Subnet where the load balancer should reside, and assign an IP address.
4.  **Listener Configuration:** Specify the protocol (e.g., HTTP) and port (e.g., 80) for incoming traffic.
5.  **Pool Configuration:** Choose a load balancing algorithm (e.g., Round Robin).
6.  **Members:** Select the backend Compute Instances that will process the traffic and specify their listening ports.
7.  **Health Monitor:** Define the health check protocol, ping interval, and timeout thresholds.

### Public Exposure and Security

By default, a new load balancer is only accessible from within its internal subnet. 

*   **Public Access:** To make the load balancer accessible from the public internet, navigate to **Network > Floating IPs** and associate a Floating IP directly to the load balancer's VIP (Virtual IP) port.
*   **Security Groups:** Make sure that the **Security Groups** attached to your backend Compute Instances allow ingress traffic on the member ports originating from the load balancer's IP address.