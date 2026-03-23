---
sidebar_label: Images
sidebar_position: 4
---

# Images

In SovereignSecure Cloud, an **Image** is a virtual machine template containing a pre-configured operating system and potentially other software. Images are used as the base to provision new Compute Instances.

Our image service is powered by OpenStack Glance and is fully integrated into the Cloud Management Platform (CMP).

## Image Types

You can choose from several types of images when deploying a new instance:

*   **Public Images:** Standard, secure, and fully patched OS images provided and maintained by SovereignSecure Cloud administrators. These typically include popular Linux distributions (Ubuntu, CentOS, RHEL) and Windows Server environments.
*   **Private Images (Custom Images):** Images you create yourself. These are often created by taking a snapshot of an existing, pre-configured instance. Private images are only visible to users within your Project.
*   **Shared Images:** Images that have been explicitly shared between different Projects or Organizations.

## Supported Image Formats

If you are uploading your own custom image, SovereignSecure Cloud supports several standard virtual machine disk formats. The most common and highly recommended format is **QCOW2**, as it provides dynamic sizing and snapshot support.

Other supported formats include:

*   `qcow2` (QEMU copy-on-write)
*   `raw` (Unstructured disk image)
*   `iso` (Optical disk image)

!!! tip "Cloud-Init and Cloudbase-Init"
    When bringing your own custom images, we strongly recommend installing **cloud-init** (for Linux) or **Cloudbase-Init** (for Windows) before capturing the image. This ensures your instances will properly receive SSH keys, network configurations, and User Scripts upon boot.

## Creating a Custom Image

You can create a custom image from an existing running instance's root block storage to capture its exact state.

1.  Navigate to **Compute > Instances** in the Cloud Console.
2.  Select the instance you want to capture.
3.  It is highly recommended to **Stop** the instance first to ensure data integrity.
4.  Select **Create Image** from the Actions menu.
5.  Provide a name and description for your new image.

Once completed, the new image will be available in your **Compute > Images** repository and can be used to launch identical clone instances.