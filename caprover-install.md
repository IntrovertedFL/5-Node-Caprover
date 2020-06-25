* #### Generate ssh key (on node0) 

```
ssh-keygen
```

* #### Copy ssh keys to node 2,3,4,5

```
ssh-copy-id root@173.208.139.89
ssh-copy-id root@173.208.139.91
ssh-copy-id root@173.208.139.92
ssh-copy-id root@173.208.139.93
```

* #### Secure root login over SSH 

!! Make sure you are able to login to nodes 2,3,4,5 with ssh key before securing them !!

```
sudo nano /etc/ssh/sshd_config
PermitRootLogin without-password
Also  find "#PasswordAuthentication yes"
change too "PasswordAuthentication no"
```

* #### Deploy Caprover (On Node0)

```
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```

* #### Configure Caprover Via your local workstation

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
