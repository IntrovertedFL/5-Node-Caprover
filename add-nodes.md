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

* #### Login to caprover dashboard and select cluster

Retrieve private key
 
```
cat ~/.ssh/id_rsa
```
```
Enter info and make sure to join the first 4 nodes as "worker nodes"
```


