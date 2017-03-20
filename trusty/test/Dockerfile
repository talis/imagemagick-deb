FROM ubuntu:trusty

RUN apt-get update

COPY imagemagick_6.9.7-10-trusty-talis_amd64.deb /root/

RUN apt-get install -y gdebi
RUN cd /root && gdebi -n imagemagick_6.9.7-10-trusty-talis_amd64.deb
RUN /usr/local/bin/convert --version
