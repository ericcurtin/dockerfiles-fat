FROM ubuntu:14.04

ENV http_proxy=$http_proxy
ENV https_proxy=$https_proxy
ENV ftp_proxy=$ftp_proxy

RUN apt update -y &&\
    apt install -y init cmake g++ clang libpoco-dev lsb-release &&\
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

