# syntax=docker/dockerfile:1

FROM ubuntu:latest
LABEL Description="homecontroller development environment"

RUN apt-get -y update && apt-get install -y
RUN apt-get install -y g++ make cmake libssl-dev nodejs npm clang git

RUN git clone https://github.com/nodejs/llhttp.git \
    && cd llhttp \
    && npm install \
    && make \
    && make install

RUN git clone https://github.com/zaphoyd/websocketpp.git \
    && cd websocketpp \
    && mkdir build \
    && cd build \
    && cmake .. \
    && make install

RUN git clone https://github.com/Tencent/rapidjson.git \
    && cd rapidjson \
    && mkdir build \
    && cd build \
    && cmake .. \
    && make install

RUN echo "/usr/local/lib" > "/etc/ld.so.conf.d/999local.conf"
RUN ldconfig

RUN rm -r llhttp
RUN rm -r websocketpp
RUN rm -r rapidjson