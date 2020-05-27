FROM ubuntu:16.04 as builder

LABEL Description="This image is used to build hyacinth service"

LABEL version="1.0.0"

LABEL author="haixiang1977@gmail.com" date="2020-05-24"

# install dependancy
RUN apt-get update
RUN apt-get install -y build-essential cmake curl wget libssl-dev vim

# install boost dependancy
RUN mkdir -p /home/boost/install
WORKDIR /home/boost/
RUN wget -P /home/boost/ https://dl.bintray.com/boostorg/release/1.73.0/source/boost_1_73_0.tar.gz
RUN tar -xzf boost_1_73_0.tar.gz
COPY hyacinth/external/boost/install_boost.sh /home/boost/boost_1_73_0/
WORKDIR /home/boost/boost_1_73_0
RUN ./install_boost.sh

# install mosquitto dependancy
RUN mkdir -p /home/mosquitto/install
WORKDIR /home/mosquitto/
RUN wget -P /home/mosquitto/ https://mosquitto.org/files/source/mosquitto-1.4.11.tar.gz
RUN tar -xzf mosquitto-1.4.11.tar.gz
WORKDIR /home/mosquitto/mosquitto-1.4.11
RUN cmake . && \
    make && \
    make DESTDIR=../install/ install

# build hyacinth project
COPY hyacinth /home/hyacinth
WORKDIR /home/hyacinth/build
RUN ./run_build.sh build

WORKDIR /home/hyacinth/bin
CMD ./hyacinth

