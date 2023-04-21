---
title: "SDK"
weight: 0
---
You can extend Vurtigo by building your own C++ plugins using the [SDK docker image](https://hub.docker.com/r/labonny/vurtigo-sdk). This image includes Vurtigo, the Geometry Server, and the developer tools needed to build plugins. Installation requirements are the same as for the main image.

Download the image using: ``docker pull labonny/vurtigo-sdk:v320``

The SDK contains a sample plugin, "Camera Motion", in the home directory "/home/vdev/CameraMotion". A separate "Hello World" plugin is available on [github](https://github.com/WrightGroupSRI/HelloWorld.git). Follow the provided README to build these.

See the [Vurtigo Design paper](/Vurtigo_Design_320.pdf) for a high-level description of Vurtigo's design and plugin architecture.
