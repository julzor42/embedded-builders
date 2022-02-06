This repository contains a collection of Dockerfiles for building
Microchip PIC32, STM32 or ESP32 based projects *(WIP)*.

# Usage

## Build the images
### XC32
```
docker build -t xc32 .
```

## Build a project
If your project contains a Makefile:
```
docker run -v`pwd`:/project xc32 make
```

# Platforms
## xc32
* Latest version from Microchip

## stm32
* gcc-arm-none-eabi
* libopencm3 installed in /opt/libopencm3