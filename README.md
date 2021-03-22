## An exploration of container scanning and container pentesting tools

## Container WORST practice
Image creation (dockerfile)
- execute container as root user `USER root`
- enable an ssh daemon
- include an executable with `setuid` or `setgid` bit
- confidential data in build file

Container deployment (`docker run`)
- mount to unix socket `-v /var/run/docker.sock:/var/run/docker.sock`
- mount to other sensitive directories `-v /proc:/proc`, `-v /dev:/dev`, `-v /etc:/etc`
- run as privileged `--privileged`
- add capabilities `--cap-add all`
