FROM debian

MAINTAINER julien delmotte <mail@julz.fr>

ENV DEBIAN_FRONTEND noninteractive

# Instal dependencies

RUN apt-get update -yq \
    && apt-get upgrade -yq \
    && apt-get install -yq --no-install-recommends git zlib1g-dev libtool flex \
    bison libgmp3-dev libmpfr-dev libncurses5-dev libmpc-dev \
    autoconf texinfo build-essential libftdi-dev

RUN apt-get install -yq python3

# Install gcc

RUN apt-get install -yq gcc-arm-none-eabi

# Download and install libopencm3
RUN git clone https://github.com/libopencm3/libopencm3 /opt/libopencm3 \
    && cd /opt/libopencm3 \
    && make

RUN useradd user
USER user

VOLUME /project
WORKDIR /project

RUN arm-none-eabi-gcc --version
