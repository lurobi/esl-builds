FROM nvidia/cuda:11.1-devel-ubuntu20.04
#LABEL maintainer "robison@arlut.utexas.edu"
#RUN apt-get update

# Julia's CUDA.jl package requires libcuda.so, but the ld.so.conf cuda file
# doesn't include the directory which contains libcuda.so, (but it does 
# include the /usr/local/cuda-11.1/targets/x86_64-linux/lib directory, where
# most everything else lives).
RUN echo "/usr/local/cuda-11.1/compat" >> /etc/ld.so.conf.d/999_cuda-11-1.conf
RUN apt-get update && DEBIAN_FRONTEND=noninteractive \
  apt-get install -y --no-install-recommends \
  build-essential wget julia python3 python3-pip cmake xorg-dev
RUN julia -e 'import Pkg; Pkg.add(["CUDA","AbstractFFTs","BenchmarkTools","Revise","Gtk","CairoMakie","HDF5"])'


# RUN apt-get update && apt-get install -y --no-install-recommends \
#   build-essential curl \
#   libhdf5-dev libhdf5-103 \
#   gfortran gcc \
#   python3 python3-minimal python3-pip \
#   scons git \
#   libfftw3-3 libfftw3-dev \
#   gdb 
#     # && rm -rf /var/lib/apt/lists/*

# RUN pip3 install fortran-language-server

# ENV NCCL_VERSION 2.7.8
# RUN apt-get update && apt-get install -y --no-install-recommends \
#     cuda-libraries-11-1=11.1.0-1 \
#     libnpp-11-1=11.1.1.269-1 \
#     cuda-nvtx-11-1=11.1.74-1 \
#     libcublas-11-1=11.2.1.74-1 \
#     libnccl2=$NCCL_VERSION-1+cuda11.1 \
#     && apt-mark hold libnccl2
#    && rm -rf /var/lib/apt/lists/*
