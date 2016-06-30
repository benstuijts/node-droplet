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

adduser deploy
adduser deploy sudo # or wheel if sudo doesn't exist
exit
```

```linux
# local laptop
brew install ssh-copy-id                            # needed on OS X
ssh-copy-id -i ~/.ssh/ssh_key_file "deploy@104.236.44.57 -p 22" # this will prompt for the password

windows:
ssh user@lnxhost "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < \\path_to_where_the_file_was_generated_from_ssh_key_gen\id_rsa.pub

ssh deploy@104.236.44.57 -i ~/.ssh/ssh_key_file -p 22
> Enter passphrase for key '/Users/homestar/.ssh/ssh_key_file':
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

## More information

<a href="http://www.youtube.com/watch?feature=player_embedded&v=YZzhIIJmlE0
" target="_blank"><img src="http://img.youtube.com/vi/YZzhIIJmlE0/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="320" height="240" border="10" /></a>

## Installing Node

```linux
curl -fsSL bit.ly/nodejs-min | bash
```

## Installing Mongodb

```linux
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list

sudo apt-get update

sudo apt-get install -y mongodb-org
```

Check MongoDB Status: 
```linux
service mongod status
```
