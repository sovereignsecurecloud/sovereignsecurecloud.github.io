---
sidebar_label: User Guide
sidebar_position: 2
---

# Instance User Guide

## Create Instances
You can create instances either by using the settings below or by using Terraform/OpenTofu. To create instances using Terraform/OpenTofu, select Create Instance page. 

### OS Settings
Determine how the root block storage is created that will be used when an instance is created.

* Select either Create New and Set up or Use Existing Resource.
* If you select Create New and Set up, create root block storage using an image.
* If you select Use Existing Resource, use a previously created block storage or snapshot.

### Image
Select the image that contains the operating system you need. You can choose between public images provided by SovereignSecure Cloud, images you've previously created, or shared images.

The available instance flavors vary depending on the image you choose, so we recommended you choose an image first when creating an instance.

| OS      | OS Disk Size         |  Memory      |
| ----------- | --------------------|-----------|
| Linux       | 10GB      | 4GB     |
| Windows       | 40GB     | 4GB     |

### Root Block Storage
Set up root block storage according to the OS settings.

* If you select __Create New and Set up__, create the root block store by specifying the __block storage type__ and __block storage size__.
* If you select Use __Existing Resource__, specify the __original resource__ to use as root block storage.

### Original Resource
You can select either a previously created __block storage__ or __snapshot__.

When you select __block storage__, use the previously created block storage as the root block storage.
When you select __snapshot__, the root block storage is created using a previously created snapshot.

### Block Storage Size
Specify the root block storage size of an instance.

The block storage size must be at least the minimum size required by the image.
The root block storage size varies depending on instance flavor.

| flavors      | Supported Block Storage Size         |
| ----------- | --------------------|
| g       | 10GB      |
| m       | 40GB     |

!!! note
    Because you are charged by block storage size, it is inefficient to make the default block storage size large without consideration. We recommend that you add additional block storage as needed.
    * If you select block storage for Use Existing Resource in the OS settings, you can't change the block storage size.
    * If you select snapshot for Use Existing Resource in the OS settings, block storage size must be set equal to or larger than the original block storage size.

### Block Storage Type
Determines the default block storage type of an instance.

Choose either HDD or SSD. The choice of block storage type affects pricing and performance.
You cannot change the block storage type once the instance is created.

!!! note
    If you select Use Existing Resource in the OS settings, you can't change the block storage type.

### Availability Zone
If an availability zone is not specified, a random zone is selected. An instance can use a block storage only if they both exist in the same availability zone. If the block storage you wish to use exists in a particular availability zone, then select that zone.

!!! note
    * Resources in a VPC can be used in any availability zone.
    * If you select Use Existing Resource in the OS settings, you can't change the availability zone.

For more details on availability zones, see Availability Zone in Instance Overview.

### Flavor
You can select various flavors depending on virtual hardware performance specifications. However, the choice of some flavors may be limited depending on the virtual hardware performance that your image requires. For more details, see Instance Overview.

!!! note 
    1 vCPU refers to one socket composed of one thread and one core, the number of threads and the number of cores per socket are constant, one each.

Instance flavors can be changed in the SovereignSecure Cloud console even after instance creation, from higher to lower specs and vice versa. However, note that some flavors cannot be changed. See Modify flavor for details.

!!! warning
     An instance's root block storage cannot be changed by changing instance flavors.

### Number of Instances
You can specify the number of instances you want to create when creating multiple instances with the same image, availability zone, flavor, block storage size, key pair, and network settings. The instance names will be the name you specified, with numbers such as -1 and -2 appended to the end. For example, creating two instances named my-instance will result in my-instance-1 and my-instance-2. The maximum number of instances you can create at once is 10.

When you create multiple instances without specifying an availability zone, each instance will be created in a randomly selected availability zone. For example, if two instances are created without specifying an availability zone, they may be created in the same zone or they may be created in different zones. If all instances need to be created in the same availability zone, select a particular zone.

!!! note 
    If you select block storage for Use Existing Resource in the OS settings or Use Existing Network Interface in the network settings, the number of instances is limited to 1.

### Key Pair
Use an existing key pair or create a new key pair. To register an existing key pair, see Import Key Pair (Windows) for Windows users, and Import Key Pair (Mac and Linux) for Mac and Linux users.

!!! note 
    Key Pair is a resource assigned to the user account, so it's not deleted when you delete a project.

### Network
Select a subnet defined in your VPC to connect to an instance. For each selected subnet, a network interface is created in the instance to connect to that subnet. You can change the order of selected subnets to change network interfaces, in which case the first network interface (eth0) will be set as the default gateway.

For more details on creating and managing networks, refer to VPC Overview.

### Floating IP
Select whether you will use a floating IP after instance creation. If you enable this option, a new floating IP is created and connected to the first network interface. Note that the first network interface must be connected to a subnet where an internet gateway is configured.

Floating IP can be managed from Instance > Management, or Instance > Floating IP. For more details on floating IP, see VPC Console Guide.

### Security Group
Select security groups that the instance will be included in. One instance can be included in multiple security groups, in which case,

* The instance can communicate over the network with all other instances included in each security group. When you are dealing with an instance with sensitive data that is not meant to be accessible by other instances, you must carefully select security groups.
* The rules of each security group are aggregated and applied to the instance's external network communication.

For more details on security groups, see VPC Console Guide.

### Additional Block Storage
Select whether you will attach an additional block storage after instance creation. If you enable this option, a new block storage separate from the root block storage is created and attached to the instance. As with the root block storage, you can specify the name, storage type, and size of the additional block storage you create.

By using the root block storage only for the OS and storing your frequently used applications and data on the additional block storage, you can easily migrate or copy your applications and data using the block storage attach/detach and snapshot features. In addition, when an instance failure occurs, you can easily recover your services by simply detaching the additional block storage and attaching it to another instance.

Block storage can also be managed from Instance > Block Storage. For more details on block storage, see Block Storage Guide.

### Placement Policy
You can use placement policies to place instances on different hypervisors. When you set a placement policy at instance creation time, instances assigned to the same placement policy are created on different hypervisors.

!!! warning
    Instance creation may fail in situations where distributed deployment is not possible.

### User Script
You can specify a script to be executed after instance creation. The user script is executed following the instance's initial boot and after the initialization process including network configuration has completed. User scripts in SovereignSecure Cloud are executed by automated tools such as cloud-init (Linux) and Cloudbase-init (Windows), which are embedded in the official images.

!!! warning
    User scripts are executed with root (Linux)/Administrator (Windows) privileges.

#### Linux
The first line of a user script must begin with #!.

```bash
#!/bin/bash
```
...
For a user script to run successfully, log files in the instance must be checked. You can check output logs printed by standard output/error from the script in /var/log/cloud-init-output.log.

#### Windows
Windows images support both Batch and PowerShell formats for user scripts. The format is determined by an indicator specified in the first line.

* Batch Script
```batch
rem cmd
...
```

* PowerShell Script
```powershell
#ps1_sysnative
...
```
To use both Batch and PowerShell in your script, use the following format.

* EC2 format
```
<script>
...
</script>
<powershell>
...
</powershell>
```
Logs from user scripts can be found in 
>  *C:\Program Files\Cloudbase Solutions\Cloudbase-Init\log\cloudbase-init.*

For more details regarding user scripts, see the cloud-init or Cloudbase-init guides.

### Additional Instance Features
#### Change Instance Status
An instance’s status can be changed by stopping, terminating, deleting, and starting it.

For more details on hypervisor resources and fees for stopping, terminating, and deleting instances, see the table below.

| Classification | Stop instance | Terminate Instance | Delete Instance |
| -------------- | ------------- | ------------------ | --------------- |
| **Hypervisor resource** | Resource remain allocated | Resource returned and reallocated when an instance is started | Resource removed |
| **Pricing for instance** | Price for stopping applied | Free | Free |
| **Pricing for other connected resources** | Charged | Charged | Charged |

!!! note 
    GPU Instances cannot be terminated and will incur normal (100%) rates when stopped.

#### Create Image
Create an image from an instance's root block storage. It is recommended to stop instances before creating an image in order to ensure data integrity.

While it is possible to create an image from an instance that has no available free space in its root block storage, those images are unusable by other instances because they cannot be properly initialized. Before creating an image, ensure that your instance has at least 100KB of free space.

Created images are registered as private images in Compute > Image. You can use the registered image to create an instance with a block storage identical to that of the original instance.

!!! warning
    The size of the created image may be larger than the actual usage of the root block storage.

#### Associate/Disassociate Floating IP
Floating IP can be associated with or disassociated from an instance, regardless of the instance's status. If you have no available floating IP or if the floating IP you want is not available, you can create one by clicking Create. Alternatively, floating IP can also be created from Network > VPC > Floating IP.

For more details on floating IP, see VPC Overview.

#### Modify Security Group
An instance's security groups can be modified regardless of the instance's status. Modified security groups are applied immediately.

For more details on security groups, see Security Group and VPC Overview.

#### Change Network Subnet
An instance's network subnet can only be changed while the instance is stopped. When you add a subnet, a network interface that will be connected to that subnet is automatically created on your instance. If you add multiple subnets at once, the order of the newly created network interfaces on the instance is set randomly. Deleting a subnet from an instance automatically deletes the network interface that was created along with the subnet.

#### Modify Flavor
Instance flavors can be changed once an instance has been stopped. If an instance is running, click Stop Instance in Additional Features to stop the instance.

You can only change an instance to another flavor that is compatible with its current flavor.

* `m2`, `c2`, `r2`, `t2`, `x1` flavor instances can be changed to `m2`, `c2`, `r2`, `t2`, `x1` flavors.
* `m2`, `c2`, `r2`, `t2`, `x1` flavor instances cannot be changed to `u2` flavors.
* `u2` flavor instances cannot be changed to other flavors once they have been created, not even to those of the same `u2` flavor.

When you modify flavors, instance resize and resize confirmation tasks proceed. When all tasks are completed, the VM changes its status to Shutoff. You can start the instance by clicking Start Instance in Additional Features.

!!! note  
    The instance's root block storage size cannot be modified. If an instance requires additional block storage space, attach a block storage. For details on how to attach block storage, see Block Storage Overview.

Instances will be charged using the new flavor from the moment the modification completes.

#### Change Instance OS Details
You can change instance OS information regardless of the state of the instance. 

On the Compute > Instance page, click the instance whose OS information you want to change. On the Basic Information tab of that instance's details screen, click OS > Modify.

!!! note  
    You can't change the OS type.

#### Change Instance Description
You can change instance description regardless of the state of the instance. 

On the Compute > Instance page, click the instance whose information you want to change. On the Basic Information tab of that instance's details screen, click Description > Change.

#### Change Instance Key Pair
You can change the instance key pair only if the instance is active.

On the Compute > Instance page, click the instance whose key pair information you want to change. On the Basic Information tab of that instance's details screen, click Key Pair > Change.

Change the key pair of the instance default account to the selected key pair. The instance default account can be found on the Connection Information tab of the instance's bottom details screen.

!!! warning 
    Changing an instance key pair deletes all public key information in the instance except for the selected key pair.

!!! note  
    Only project members with the ADMIN permissions for the basic infrastructure can change the instance key pair, which cannot be changed if it is a Windows OS instance.

!!! note  
    If the image version used to create the instance is low, the feature to change key pairs may not be available.

#### Manage Placement Policies
You can create and delete placement policies and view a list of instances assigned to placement policies.

Only the anti-affinity placement policy type for distributed placement is provided.

You can delete a placement policy even if instances are assigned to it, in which case the instances are not deleted.

### Key Pairs
#### Import Key Pairs (Windows)
You can use puttygen, which is installed when you install the PuTTY SSH client, to create a key pair and register it with SovereignSecure Cloud.

Make sure you have PuTTY installed.

Run puttygen.

*[Image: PuTTYgen]*

Select RSA (or SSH-2 RSA in older versions of puttygen) under Parameters. Click Generate under Actions. Continuously move your mouse in the empty space in order to generate the key.

After the key is generated, the public key file contents will be visible as shown below. Paste the contents of the public key into the Public Key field in Get Key Pair in order to register the key pair.

*[Image: PuTTYgen generated key]*

Click Save private key under Actions to save the private key. If you save the private key leaving the Key passphrase field blank, the message "Are you sure you want to save this key without a passphrase to protect it?" will appear. In order to use your converted private key more securely, set a passphrase before saving.

!!! warning
    If you wish to be able to automatically login to your instance, you should not set a key passphrase. When a passphrase is used, you must manually enter the private key's passphrase during login.

The registered key pair can be used to create instances, and the key pair's private key must be used when accessing instances. For more details on how to access instances, see Instance Overview.

Just as with key pairs created from SovereignSecure Cloud, imported key pairs also need to be managed cautiously since exposed private keys can be abused by anyone to access instances.

#### Import Key Pairs (Mac and Linux)
Key pairs created using ssh-keygen in Mac or Linux can be registered with SovereignSecure Cloud. Use the following command to create a key pair.

```
$ ssh-keygen -t rsa -f my_key.key
```

You can choose to set a passphrase for the key pair, although it is not required. If you wish to use your key pair more securely, we recommend setting a passphrase. The file with .pub appended to the specified key pair name contains the public key.

```
$ cat my_key.key.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCnnUAe36txQqk8J7VzbNuYKVQQ3gbNoClndHMX49OD+1Rw5xrDFLUKQqxbBDtlNMoA9tKBZNrQBpKr1kFEtvMIj1HPkH9ocb4MbuoVVjpkIhixbKMMJPDQ4JQJxaifsjR59YsZyDAp0aXZp+o+OB97P3S4AKPY2kQR0JdSr30+6Av6smf+3mZceAE4abzklfbyWT5slP1im/wfYEPO3QBEDl/0JbmTjKWPYI6QnbwnPRHS63SJ+Kd2QeYQYJCadv7X4mXnw81qEIWq/dx1SQkGDTNgR7lnN2ApFlU5EZcow69z6tiCr0hlyigwjGooMg3wTZvcSlYcVeTzZ755RArd ...
```
Paste the contents of the public key into the Public Key field in Get Key Pair in order to register the key pair.

The registered key pair can be used to create instances, and the key pair's private key must be used when accessing instances. For more details on how to access instances, see How to Access Instances.

Just as with key pairs created from SovereignSecure Cloud, imported key pairs also need to be managed cautiously since exposed private keys can be abused by anyone to access instances.