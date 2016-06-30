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

Next create a user, add the secure key, then remove remove root and password access.

```linux
# remote server

adduser strongbad
adduser strongbad sudo # or wheel if sudo doesn't exist
exit
```

```linux
# local laptop
brew install ssh-copy-id                            # needed on OS X
ssh-copy-id -i ~/.ssh/waffles "strongbad@104.236.44.57 -p 22" # this will prompt for the password

ssh strongbad@104.236.44.57 -i ~/.ssh/waffles -p 22
> Enter passphrase for key '/Users/homestar/.ssh/waffles':
```

```linux
# remote server
sudo vim /etc/ssh/sshd_config
> Port 4242
> PermitRootLogin no
> PasswordAuthentication no
sudo service ssh restart
exit
```

```linux
sudo apt-get update
sudo apt-get upgrade -y
```


