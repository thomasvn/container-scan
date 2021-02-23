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
