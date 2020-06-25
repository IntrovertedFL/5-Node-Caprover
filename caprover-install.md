- #### Deploy Caprover (On Node0)

```
docker run -p 80:80 -p 443:443 -p 3000:3000 -v /var/run/docker.sock:/var/run/docker.sock -v /captain:/captain caprover/caprover
```

- #### Configure Caprover Via your local workstation

```
npm install -g caprover
caprover serversetup
```

- #### Example Output

```
have you already started CapRover container on your server? (Y/n) Y
IP address of your server: 192.168.254.88
CapRover server root domain: develop.yourdomain.com
new CapRover password (min 8 characters): [hidden]
enter new CapRover password again: [hidden]
"valid" email address to get certificate and enable HTTPS: me@gmail.com
/ Enabling SSL... Takes a few seconds...
CapRover machine name, with whom the login credentials are stored locally: (captain-01)
CapRover server setup completed: it is available as captain-01 at https://captain.develop.yourdomain.com

For more details and docs see CapRover.com
```
