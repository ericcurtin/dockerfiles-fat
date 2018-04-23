FROM ubuntu:18.04

ENV http_proxy=$http_proxy
ENV https_proxy=$https_proxy
ENV ftp_proxy=$ftp_proxy

RUN apt update -y &&\
    apt install -y init cmake g++ clang lsb-release git libpcre3-dev\
      libssl-dev zlib1g-dev net-tools vim curl &&\
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN cd /tmp && git clone https://github.com/nginx/nginx.git &&\
    git clone https://github.com/fdintino/nginx-upload-module.git &&\
    cd nginx && auto/configure --add-module=../nginx-upload-module &&\
    make -j3 && make -j3 install && cd /tmp && rm -rf nginx*

