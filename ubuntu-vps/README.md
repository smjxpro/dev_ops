# Ubuntu VPS Configuration

##### SSH into VPS:

`ssh root@remote_IP`

##### Add a new user:

`adduser remote-user`

##### Add the new user to sudo group:

`usermod -aG sudo remote-user`

##### Logout:

`logout`

##### SSH using new user account:

`ssh remote-user@remote_IP`

---

## Enable private key authentication

##### Create keys on the local machine:

`ssh-keygen -t rsa`

##### Copy public key to VPS:

`ssh-copy-id remote-user@remote_IP`

##### SSH again to VPS:

`ssh remote-user@remote_IP`

#### Disable root and password-based login

##### Set `PermitRootLogin no` and `PasswordAuthentication no` by editing sshd_config:

`sudo nano /etc/ssh/sshd_config`

##### Restart SSH:

`sudo systemctl restart ssh`

---

## Install Webmin

##### Add Webmin repo to apt source list:

`sudo nano /etc/apt/sources.list`

then add the following line at the end of the file:

`deb http://download.webmin.com/download/repository sarge contrib`

##### Add Webmin’s PGP key:

`sudo wget -qO- http://www.webmin.com/jcameron-key.asc | sudo apt-key add`

##### Install Webmin:

`sudo apt update`

`sudo apt install webmin`

###### Visit `https://remote_IP:10000` to access Webmin


