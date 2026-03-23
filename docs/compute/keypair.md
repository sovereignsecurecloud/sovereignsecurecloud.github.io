---
sidebar_label: Key Pairs
sidebar_position: 5
---

# Key Pairs

A **Key Pair** is a secure authentication method used to access your instances in SovereignSecure Cloud. Instead of relying on traditional passwords, which can be vulnerable to brute-force attacks, key pairs use public-key cryptography (SSH) to ensure that only authorized users can connect to compute resources.

A key pair consists of two parts:

*   **Public Key:** Stored inside your SovereignSecure Cloud project and automatically injected into your instance (typically in `~/.ssh/authorized_keys` for Linux) when it is provisioned.
*   **Private Key:** Kept securely on your local machine and used by your SSH client to prove your identity.

## Creating a New Key Pair

You can generate a new key pair directly through the Cloud Console:

1. Navigate to **Compute > Key Pairs** in the Cloud Console.
2. Click **Create Key Pair**.
3. Enter a descriptive **Name** for your key pair.
4. Select the **Key Type** (SSH is standard).
5. Click **Create**.
6. **Important:** Your browser will automatically download the Private Key (typically a `.pem` file). This is the *only* time you will be able to download this private key. Store it in a secure location on your local machine.

## Importing an Existing Key Pair

If you already have your own SSH key pair generated via `ssh-keygen` (Linux/macOS) or PuTTYgen (Windows), you can import the public key into the platform.

1. Navigate to **Compute > Key Pairs**.
2. Click **Import Key Pair**.
3. Enter a **Name** to identify this key pair.
4. Paste the contents of your **Public Key** (e.g., the contents of your `id_rsa.pub` or `id_ed25519.pub` file) into the provided text box.
5. Click **Import**.

## Connecting to Your Instance

Once your instance is running and has an assigned Floating IP, you can connect to it using your private key.

### Linux / macOS

Open your terminal and use the `ssh` command, specifying the path to your private key file using the `-i` flag:

```bash
chmod 400 my-private-key.pem  # Ensure the key has strictly secure permissions
ssh -i /path/to/my-private-key.pem username@<Instance-Floating-IP>
```

*(Note: The default `username` depends on the Image used, such as `ubuntu`, `centos`, `cloud-user`, or `debian`)*.

### Windows (PuTTY)

1. Open **PuTTY**.
2. In the **Host Name (or IP address)** field, enter the instance's Floating IP address.
3. In the left-hand menu, navigate to **Connection > SSH > Auth > Credentials**.
4. Click **Browse** and select your private key file (PuTTY requires the `.ppk` format. If you downloaded a `.pem` file, use PuTTYgen to convert it).
5. Click **Open** to initiate the connection.