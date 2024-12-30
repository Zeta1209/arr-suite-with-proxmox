# arr-suite-with-proxmox
Quick guide for install some services from the Arr suite on Proxmox. Also setting up network drive from a NAS.

## On the NAS
  1. Turn on NFS Share (NFS is better than SMB for Linux systems, otherwise you could use SMB)
  2. Add NFS permissions for the concerned folder
    2.1 In my case, my local network is 10.0.0.1/24 so I'll use 10.0.0.* which will allow all host from 10.0.0.1 to 10.0.0.255
  3. Apply all your changes and take not of the path (ex: Volume1/Media)

## On Proxmox

  1. Create a folder to mount your NAS:
     '''bash
     mkdir /mnt/MyNAS/ && mkdir /mnt/MyNAS/Media
  2. Then you need to manually mount the shared folder:
     '''bash
     mount -t nfs -o vers=4.1 nas-ip-address:/Volume1/Media /mnt/MyNAS/Media
  3. You also need to edit the permission of the folder:
     '''bash
     chmod -R 777 /mnt/MyNAS/Media
