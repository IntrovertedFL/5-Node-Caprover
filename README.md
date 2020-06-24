# 5-Node-Caprover-Swarm

1. Install/Configure 5 VM's (I used Proxmox/Ubuntu 18.04 VM's)

* ### Configure hosts

```nano /etc/hosts
```
```sh
Sample

127.0.0.1       localhost
192.168.254.88  master.tribestudios.io  master

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes ff02::2 ip6-allrouters
192.168.254.89 - node01.tribestudios.io node01
192.168.254.91 - node02.tribestudios.io node02
Enable Passwordless Sudo
sudo nano /etc/sudoers
Find the line which contains #includedir /etc/sudoers.d
Below that line add: username ALL=(ALL) NOPASSWD: ALL
Disable Swap
swapoff -a
nano /etc/fstab
Comment out line "#/dev/mapper/master--vg-swap_1 none            swap    sw              0       0"
reboot and make sure it's off.
do "free -h" and make sure swap says "0"
```
