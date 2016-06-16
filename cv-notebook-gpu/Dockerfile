FROM kostyaev/cv-base-gpu
MAINTAINER Dmitry Kostyaev dmitry@kostyaev.me

RUN apt-get update && pip install --upgrade virtualenv && pip install -U jupyter

RUN apt-get update &&  pip install --upgrade pip \
&& pip install --upgrade virtualenv \
&& pip install -U jupyter

EXPOSE 8888
WORKDIR /opt
CMD ipython notebook --ip 0.0.0.0 --no-browser
