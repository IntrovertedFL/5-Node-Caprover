# Install/Configure 5 VM's (Ubuntu 16.04LTS)

- #### Update

```
apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y && apt-get install qemu-guest-agent -y
```

- #### Enable root login

```
sudo su -
passwd (create password for root)
nano /etc/ssh/sshd_config
PermitRootLogin yes
```

- #### Firewall Config (Using default ssh port 22)

```
ufw enable
ufw allow 22,80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
reboot and make sure you can login
```

- #### Set Host

```
export USE_HOSTNAME=dog.example.com

echo $USE_HOSTNAME > /etc/hostname

hostname -F /etc/hostname
```

- #### Configure Host File

```
nano /etc/hosts

127.0.0.1       localhost
192.168.254.88  node0.yourdomain.com
192.168.254.89  node1.yourdomain.com
192.168.254.91  node2.yourdomain.com
192.168.254.92  node3.yourdomain.com
192.168.254.93  node4.yourdomain.com
```

- #### Install Docker

```
curl -fsSL get.docker.com -o get-docker.sh

# Install Docker using the stable channel (instead of the default "edge")

CHANNEL=stable sh get-docker.sh

# Remove Docker install script

rm get-docker.sh
```

# [3. Caprover Install](https://github.com/TechGuyTN/5-Node-Caprover-Swarm/blob/master/caprover-install.md)
