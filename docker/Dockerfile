FROM ubuntu:22.04
RUN apt-get -y update && apt-get -y install sudo apt-utils
RUN groupadd ubuntu && useradd -rm -d /home/ubuntu -s /bin/bash -g ubuntu -G sudo -u 1000 ubuntu -p "$(openssl passwd -1 u)"
USER ubuntu
WORKDIR /home/ubuntu