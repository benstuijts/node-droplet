# node-droplet
Commands to spin up a digital ocean droplet

## Create SSH Key
```linux
ssh-keygen
```

Create the droplet and ssh in:
```linux
ssh root@112.123.123.23 -i ssh_key_file.pub
```

##Secure the Server

```linux
# on the remote server

sudo apt-get update
sudo apt-get install -y fail2ban
```




