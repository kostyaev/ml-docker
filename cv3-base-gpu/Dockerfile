FROM nvidia/cuda:7.5-cudnn5-devel-ubuntu14.04
MAINTAINER dmitry@kostyaev.me

ENV PYTHON_VERSION 2.7
ENV NUM_CORES 8

# Install Dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential cmake git wget unzip gfortran \
        libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev \
        libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev \
        libatlas-base-dev libboost-all-dev libgflags-dev libgoogle-glog-dev \ 
        libhdf5-serial-dev libleveldb-dev liblmdb-dev \
        libprotobuf-dev libsnappy-dev \
        protobuf-compiler pkg-config \
        python$PYTHON_VERSION-dev python-numpy python-pip python-scipy && \
    rm -rf /var/lib/apt/lists/*

RUN pip install numpy matplotlib

# Install OpenCV
RUN wget https://github.com/Itseez/opencv/archive/3.1.0.zip -O opencv3.zip && \
    unzip -q opencv3.zip && mv /opencv-3.1.0 /opencv
RUN wget https://github.com/Itseez/opencv_contrib/archive/3.1.0.zip -O opencv_contrib3.zip && \
    unzip -q opencv_contrib3.zip && mv /opencv_contrib-3.1.0 /opencv_contrib

RUN mkdir /opencv/build
WORKDIR /opencv/build

RUN rm -r /usr/bin/python3.4

RUN cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D BUILD_PYTHON_SUPPORT=ON \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=OFF \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=/opencv_contrib/modules \
    -D BUILD_EXAMPLES=OFF \
    -D BUILD_NEW_PYTHON_SUPPORT=OFF \
    -D WITH_IPP=OFF \
    -D WITH_V4L=ON ..

RUN make -j$NUM_CORES
RUN make install
RUN ldconfig
RUN cp lib/cv2.so /usr/local/lib/python$PYTHON_VERSION/dist-packages/
# Define default command.
CMD ["bash"]
