---
title: "Install"
image: "null.png"
weight: 0
---
# Install instructions
The current version of Vurtigo is available as docker image for Linux systems with an X server.

## Install docker
- Install docker via the [repository method](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
- Add your account to a docker group so you don't need to run docker with sudo as described [here](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)
## Graphics drivers
- If you are using the nvidia proprietary drivers, [install and set up the nvidia container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit) to work with docker
  - We recommend using graphics drivers that are maintained by your system (rather than downloading them directly from the vendor)
  - On Ubuntu, for example, you would do this by launching "Software & Updates" and selecting a graphics driver from the "Additional Drivers" tab
- Make sure to restart the docker daemon after configuration changes
 `sudo systemctl restart docker`
## Install x11docker
Install [x11docker](https://github.com/mviereck/x11docker#installation):
```
git clone https://github.com/mviereck/x11docker.git
cd x11docker
sudo ./x11docker --install
```
This tool simplifies display sharing for containerized applications and manages a home directory so Vurtigo settings and storage persist across sessions.
## Install vurtigo
- Download the image from [dockerhub](https://hub.docker.com/):
```
docker pull labonny/vurtigo:v320
```
## Run vurtigo
- Run it with x11docker (remove the "--runtime=nvidia" if you are not using the nvidia runtime drivers):
`x11docker -m --gpu --runtime=nvidia --network --xauth=trusted -- -p 1777:1777 -p 18946:18946 -- labonny/vurtigo:v320`
- To allow vurtigo to access folders in your host machine, you can share them using the "--share" option, for example:
`x11docker -m --gpu --share /home/myname/Data --runtime=nvidia --network --xauth=trusted -- -p 1777:1777 -p 18946:18946 -- labonny/vurtigo:v320`