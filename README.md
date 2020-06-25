# Configure DNS

* #### Configure DNS "a" record 

```
Add dns "a" record ( *.develop.techguytn.com )
```

# Install/Configure 5 VM's (Ubuntu 16.04LTS)

* #### Enable root login on nodes 2,3,4,5 (Not needed on single node install)

```
sudo su -
passwd (create password for root)
nano /etc/ssh/sshd_config
PermitRootLogin yes
```

* #### Generate ssh key (on node0) 

```
ssh-keygen
```

* #### Copy ssh keys to node 2,3,4,5

```
ssh-copy-id root@173.208.139.88
ssh-copy-id root@173.208.139.89
ssh-copy-id root@173.208.139.91
ssh-copy-id root@173.208.139.92
ssh-copy-id root@173.208.139.93
```


* #### Secure root login over SSH (Not needed on single node install)

!! Make sure you are able to login to nodes 2,3,4,5 with ssh key before securing them !!

```
sudo nano /etc/ssh/sshd_config
PermitRootLogin without-password
```

* #### Firewall Config (Using default ssh port 22)

```
ufw enable
ufw allow 22,80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
```

* #### Set Host 

```
export USE_HOSTNAME=dog.example.com
Set up the server hostname
echo $USE_HOSTNAME > /etc/hostname
hostname -F /etc/hostname
```

* #### Configure Host File (/etc/hosts)

```
127.0.0.1       localhost
173.208.139.88  node0.techguytn.com
173.208.139.89  node1.techguytn.com
173.208.139.91  node2.techguytn.com
173.208.139.92  node3.techguytn.com
173.208.139.93  node4.techguytn.com
```

* #### Install Docker

```
curl -fsSL get.docker.com -o get-docker.sh

# Install Docker using the stable channel (instead of the default "edge")
CHANNEL=stable sh get-docker.sh

# Remove Docker install script
rm get-docker.sh
sudo usermod -aG docker aaron
```

* #### Check and confirm that DNS record has Propagated 

```
Visit - https://dnschecker.org/#A
Enter your domain [develop.techguytn.com] and make sure setting "A"
Click Search. 
```

* #### Deploy Caprover (On Node0)

```
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```

* #### Configure Caprover Via Host Terminal (my desktop using vscode/powershell)

```
npm install -g caprover
caprover serversetup
```

* #### Example Output

```
have you already started CapRover container on your server? (Y/n) Y
IP address of your server: 173.208.139.88
CapRover server root domain: develop.techguytn.com
new CapRover password (min 8 characters): [hidden]
enter new CapRover password again: [hidden]
"valid" email address to get certificate and enable HTTPS: mrholttn@gmail.com
/ Enabling SSL... Takes a few seconds...
CapRover machine name, with whom the login credentials are stored locally: (captain-01)
CapRover server setup completed: it is available as captain-01 at https://captain.develop.techguytn.com

For more details and docs see CapRover.com
```
