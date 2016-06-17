FROM nvidia/cuda:7.5-cudnn5-devel-ubuntu14.04
MAINTAINER dmitry@kostyaev.me

# Install Dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential cmake git wget unzip vim gfortran \
        libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev \
        libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev \
        libatlas-base-dev libboost-all-dev libgflags-dev libgoogle-glog-dev \ 
        libhdf5-serial-dev libleveldb-dev liblmdb-dev libprotobuf-dev libsnappy-dev libopencv-dev \
        protobuf-compiler pkg-config \
        python-dev python-numpy python-pip python-scipy python-opencv && \
    rm -rf /var/lib/apt/lists/*

RUN pip install numpy matplotlib

# Define default command.
CMD ["bash"]
