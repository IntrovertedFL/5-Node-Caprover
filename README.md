# 5-Node-Caprover-Swarm

* ### 1. Install/Configure 5 VM's (I used Proxmox/Ubuntu 18.04 VM's)

* ### 2. Firewall Config 

```
ufw enable
ufw allow 80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
```

* ### 3. Set Host 

```
export USE_HOSTNAME=dog.example.com
Set up the server hostname
echo $USE_HOSTNAME > /etc/hostname
hostname -F /etc/hostname
```

* ### 4. Install Docker

```
curl -fsSL get.docker.com -o get-docker.sh
# Install Docker using the stable channel (instead of the default "edge")
CHANNEL=stable sh get-docker.sh
# Remove Docker install script
rm get-docker.sh
```
