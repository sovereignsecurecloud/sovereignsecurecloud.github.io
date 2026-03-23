# Quick Start Guide

Welcome to SovereignSecure Cloud! This Quick Start Guide is designed to help new users rapidly onboard and begin utilizing our secure and sovereign cloud services. By following these steps, you'll learn how to access the Cloud Console (powered by ManageIQ), understand its basic layout, and deploy your first cloud resource.

Our goal is to simplify your initial experience, focusing on essential tasks to get you up and running quickly.

## Prerequisites

Before you begin, ensure you have:

*   **SovereignSecure Cloud Account:** Your organization should have provided you with login credentials.
*   **Internet Access:** A stable internet connection to access the Cloud Console.

## Step 1: Accessing the Cloud Console

The SovereignSecure Cloud Console is your central hub for managing all your cloud resources.

1.  **Open your web browser** and navigate to the Cloud Console URL: `https://portal.sovereignsecurecloud.com`
2.  **Enter your Username and Password** provided by your administrator. If your organization uses Single Sign-On (SSO), you may be redirected to your corporate login page.
3.  Click **Login**.

Upon successful login, you will be directed to your personalized dashboard.

## Step 2: Understanding the Dashboard

The dashboard provides an overview of your allocated resources, active services, and any pending requests. Key areas you'll notice include:

*   **Service Catalog:** Browse and order pre-defined cloud services.
*   **My Services:** View and manage the services you have already provisioned.
*   **Resource Utilization:** Monitor your CPU, memory, and storage usage.
*   **Notifications & Alerts:** Stay informed about system events and important updates.

## Step 3: Launching Your First Virtual Machine (VM)

Let's deploy a basic Linux VM using the Service Catalog.

1.  From the dashboard, click on **Service Catalog** or navigate to **Cloud Management (CMP) > Service Catalogs**.
2.  Browse the available services and select a **"Basic Linux VM"** or similar offering.
3.  **Fill in the required details** in the provisioning form:
    *   **Service Name:** A unique name for your VM (e.g., `my-first-vm`).
    *   **Flavor:** Choose a small instance size (e.g., `t1.micro`).
    *   **Image:** Select a public Linux image (e.g., `Ubuntu 22.04 LTS`).
    *   **Network:** Select a default network or subnet if available.
    *   **Key Pair:** Choose an existing key pair or create a new one for SSH access.
4.  Review your selections and click **Order** or **Provision**.

Your request will be submitted, and the CMP will begin provisioning your VM. You can track its status under **My Services**.

## Step 4: Next Steps

Congratulations! You've successfully launched your first cloud resource. To continue your journey:

*   **Connect to Your Instance:** Learn how to securely access your newly created VM via SSH.
*   **Manage Your Resources:** Explore the full capabilities of the Cloud Management Platform.
*   **Explore Core Services:** Dive deeper into Compute, Storage, and Networking options.
*   **Automate with APIs:** Discover how to integrate and automate your workflows using our APIs.
