FROM kostyaev/cv2-base-gpu
MAINTAINER dmitry@kostyaev.me

ENV BLAS=/opt/openblas/lib/libopenblas.a
ENV PATH=$PATH:/opt/openblas/lib/

# Install Dependencies
RUN cd /opt && git clone https://github.com/xianyi/OpenBLAS && cd OpenBLAS && make FC=gfortran && sudo make PREFIX=/opt/openblas install \
&& echo /opt/openblas/lib > /etc/ld.so.conf.d/openblas.conf \
&& echo /opt/openblas/lib/libopenblas.a >> /etc/ld.so.conf.d/openblas.conf \
RUN ldconfig
# Define default command.
CMD ["bash"]
