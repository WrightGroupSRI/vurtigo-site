---
title: "Install"
draft: true
image: "null.png"
weight: 0
---
# Install instructions
The current version of Vurtigo is available as docker image for Linux systems with an X server.

## Install docker
- Install docker via the [repository method](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
- You can add your host machine user to a docker group so you don't need to run docker with sudo as described [here](https://docs.docker.com/engine/install/linux-postinstall/) or you can [set up docker to run in root-less mode](https://docs.docker.com/engine/security/rootless/) as a non-root user - this second option is more secure
## Graphics drivers
- If you are using the nvidia proprietary drivers, [install the nvidia container toolkit](https://docs.nvidia.com/ai-enterprise/deployment-guide/dg-docker.html#enabling-the-docker-repository-and-installing-the-nvidia-container-toolkit) and [add the nvidia runtime](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/user-guide.html#adding-the-nvidia-runtime) to docker using any of the three provided methods
- Make sure to restart the docker daemon after configuration changes
 `sudo systemctl restart docker`
## Install x11docker
Install [x11docker](https://github.com/mviereck/x11docker#installation):
```
git clone https://github.com/mviereck/x11docker.git
sudo ./x11docker --install
```
## Install vurtigo
- Download the image from [dockerhub](https://hub.docker.com/):
```
docker pull labonny/vurtigo:v320
```
## Run vurtigo
- Run it with x11docker (remove the "--runtime=nvidia" if you are not using the nvidia runtime drivers):
`x11docker -m --gpu --runtime=nvidia --network -- -p 1777:1777 -p 18946:18946 -- labonny/vurtigo:v320`
- To allow vurtigo to access folders in your host machine, you can share them using the "--share" option, for example:
`x11docker -m --gpu --share /home/myname/Data --runtime=nvidia --network -- -p 1777:1777 -p 18946:18946 -- labonny/vurtigo:v320`