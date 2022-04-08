---
description: >-
  In this section we detail mounting persistent disks to existing Compute Engine
  instances, useful in reserving additional space for node history.
---

# Extending compute engine storage&#x20;

Oh no, you allocated 20GB of storage for your collator node and here you are a month and a half later, off chain and out of storage.  Don't `panic!` -- deploying, mounting, and using an additional disk for your node history is easier than you think.\
&#x20;

### Initialize disk

We'll begin by initializing a new disk.  We recommend using an ssd if your node is maintaining a complete chian history.  The node will be appending data frequently and the additional throughput goes a long way, especially if you're running multiple nodes on the same instance.  &#x20;

`gcloud compute disks create <disk name> --type=<disk type> --size=<disk size> --zone=<zone name>`

#### Example:

> `gcloud compute disks create pendulum-storage --type=pd-ssd --size=100GB --zone=europe-west3-c`

### Attach disk

Next we need to attach the new disk to our instance.

> `gcloud compute instances attach-disk <compute engine name> --disk=<disk name> --zone=<zone name>`

#### Example:

> `gcloud compute instances attach-disk pendulum-collator --disk=pendulum-storage --zone=europe-west3-c`

### Mount disk

We'll need to format and mount our disk before we can use it.  For this step we'll need to aquire a shell with sudo permissions on our instance.  There are a number of ways to do this, but we recommend using ssh.

Once you have a shell with sudo permissions, we'll need to observe our storage devices.  In the following example, we're interested in /dev/sdb, as this is the 100GB disk we created and mounted in the previous steps.

> `lsblk`

#### Example output:

> `sda 8:0 0 50G 0 disk`&#x20;
>
> `├─sda1 8:1 0 49.9G 0 part /`&#x20;
>
> `├─sda14 8:14 0 4M 0 part`&#x20;
>
> `└─sda15 8:15 0 106M 0 part /boot/efi`&#x20;
>
> `sdb 8:16 0 100G 0 disk`

Now that we've identified our disk, it's time to mount it.  We'll begin by formatting our device with a lazy ext4 filesystem with no reserved space for the root volume.  We'll then create a new directory to mount our device and finally perform the mounting.

#### Format the disk:

> `sudo mkfs.ext4 -m 0 -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/sdb`

#### Create mount directory:

> `sudo mkdir /mnt/disks/pendulum-storage`
>
> `sudo chmod a+w /mnt/disks/pendulum-storage`

#### Mount the disk:

> `sudo mount -o discard,defaults /dev/sdb /mnt/disks/pendulum-storage`

### Update fstab

Finally, we'll want to update our filesystem table to include the uuid of our new table entry.  This will allow use to automatically and persistently mount our device when rebooting.&#x20;

> `sudo blkid /dev/sdb | sudo tee -a /etc/fstab`

We now have a persistent disk, ready for our parachain to write to.
