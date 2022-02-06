embedded-builders

This repository contains a collection of Dockerfiles for building
Microchip PIC32, STM32 or ESP32 based projects (WIP).

= Usage

== Build the images
Example for Microchip XC32
```
docker build -t xc32 github.com/julzor42/embedded-builders/xc32
```

== Build a project
If your project contains a Makefile:
```
docker run -it --rm --privileged -v`pwd`:/project xc32 make
```

== XC32
* Downloads an install the latest version of xc32-gcc from Microchip
* Downloads the Core32 PIC32 from git to /opt/core32
