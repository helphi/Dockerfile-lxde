FROM ubuntu:xenial

MAINTAINER helphi

ENV LANG=C.UTF-8 \
    TZ=Asia/Shanghai 

RUN apt-get update &&\
    DEBIAN_FRONTEND=noninteractive apt-get install -y lxde-core xvfb x11vnc &&\
    apt-get clean &&\
    rm -rf /var/lib/apt/lists/*

RUN echo "export DISPLAY=:1" > /root/start.sh &&\
    echo "export HOME=/root" >> /root/start.sh &&\
    echo "Xvfb :1 -screen 0 1024x768x24 &" >> /root/start.sh &&\
    echo "lxsession &" >> /root/start.sh &&\
    echo "x11vnc -display :1 -forever" >> /root/start.sh

EXPOSE 5900

CMD ["sh", "/root/start.sh"]

LABEL org.label-schema.docker.cmd="docker run -it -p 5900:5900 helphi/lxde:xenial"