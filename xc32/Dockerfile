FROM debian

MAINTAINER julien delmotte <mail@julz.fr>

ENV DEBIAN_FRONTEND noninteractive
ENV PATH $PATH:/opt/microchip/xc32/bin

# Install i386 architecture compatability and required dependencies

RUN dpkg --add-architecture i386 \
    && apt-get update -yq \
    && apt-get upgrade -yq \
    && apt-get install -yq --no-install-recommends build-essential bzip2 cpio curl python unzip wget \
    libc6:i386 libx11-6:i386 libxext6:i386 libstdc++6:i386 libexpat1:i386 \
    libxext6 libxrender1 libxtst6 libgtk2.0-0 libxslt1.1 libncurses5-dev git

RUN apt-get install -yq apt-transport-https ca-certificates -y \
    && update-ca-certificates

# Download and install xc32

RUN curl -fSL -o /tmp/xc32.run "https://www.microchip.com/mplabxc32linux" \
    && chmod a+x /tmp/xc32.run \
    && /tmp/xc32.run --mode unattended --unattendedmodeui none \
        --netservername localhost --LicenseType FreeMode --prefix /opt/microchip/xc32 \
    && rm /tmp/xc32.run

# Dowload additionnal libraries
RUN git clone https://github.com/julzor42/core32 /opt/core32

VOLUME /project
WORKDIR /project

RUN useradd user
USER user

RUN [ -x /opt/microchip/xc32/bin/xc32-gcc ] && xc32-gcc --version
