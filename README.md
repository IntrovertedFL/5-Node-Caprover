# 5-Node-Caprover-Swarm

1. Install/Configure 5 VM's (I used Proxmox/Ubuntu 18.04 VM's)

2. Firewall Config 

```sh
ufw enable
ufw allow 80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
