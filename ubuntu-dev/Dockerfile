FROM ubuntu:focal as ubuntu_apt
#LABEL maintainer "robison@arlut.utexas.edu"
#RUN apt-get update

# FROM ubuntu_apt
# FROM ubuntu_dev

# this is unncessary:
# COPY ./vscode_server.sh /tmp/vscode_server.sh
#RUN /bin/bash /tmp/vscode_server.sh

# The noninteractive part is necessary for tzdata required by emacs-nox, which *really* wants to know
# what timezone you are in, and introduces a blocking read which breaks the build.
RUN apt-get update && DEBIAN_FRONTEND=noninteractive \
 apt-get install -yq --no-install-recommends \
 build-essential curl \
 libhdf5-dev libhdf5-103 \
 gfortran gcc gdb \
 python3 python3-minimal python3-pip \
 scons git \
 libfftw3-3 libfftw3-dev \
 nano emacs-nox vim
   # && rm -rf /var/lib/apt/lists/*

RUN pip3 install fortran-language-server

#ENV NCCL_VERSION 2.7.8
#RUN apt-get update && apt-get install -y --no-install-recommends \
#    cuda-libraries-11-1=11.1.0-1 \
#    libnpp-11-1=11.1.1.269-1 \
#    cuda-nvtx-11-1=11.1.74-1 \
#    libcublas-11-1=11.2.1.74-1 \
#    libnccl2=$NCCL_VERSION-1+cuda11.1 \
#    && apt-mark hold libnccl2 \
#    && rm -rf /var/lib/apt/lists/*

