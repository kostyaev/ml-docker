FROM kostyaev/cv2-base-gpu-mp
MAINTAINER Dmitry Kostyaev dmitry@kostyaev.me

ENV CAFFE_ROOT=/opt/caffe
WORKDIR $CAFFE_ROOT
ENV CLONE_TAG=master

RUN git clone -b ${CLONE_TAG} --depth 1 https://github.com/kostyaev/caffe-augmentation-extension.git . && \
    for req in $(cat python/requirements.txt) pydot; do pip install $req; done
RUN cd /opt/caffe && mkdir build && cd build && \
    cmake -DUSE_CUDNN=1 -DBLAS=open .. && \
    make -j"$(nproc)"


ENV PYCAFFE_ROOT $CAFFE_ROOT/python
ENV PYTHONPATH $PYCAFFE_ROOT:$PYTHONPATH
ENV PATH $CAFFE_ROOT/build/tools:$PYCAFFE_ROOT:$PATH
RUN echo "$CAFFE_ROOT/build/lib" >> /etc/ld.so.conf.d/caffe.conf && ldconfig

