###BACnet openstack image
###v0.8.3

FROM ubuntu:latest

MAINTAINER Javier Benitez "javier.benitezf51@gmail.com"

#Dependencies
RUN apt-get update
RUN apt-get install -y wget git subversion
RUN apt-get install -y make gcc
RUN apt-get install libcurl4-openssl-dev

#Get and compile bacnet-stack
RUN svn -q checkout https://svn.code.sf.net/p/bacnet/code/tags/bacnet-stack-0.8.3/ bacnet-stack
RUN cd /bacnet-stack && make clean all -s

RUN mkdir /bacnet-stack/dev && cd /bacnet-stack/dev
    && git clone https://github.com/rscada/libmbus.git mbus

RUN cd /bacnet-stack/dev/mbus && ./build

#Install jansson lib
RUN wget http://www.digip.org/jansson/releases/jansson-2.10.tar.gz 
    && tar xf jansson-2.10.tar.gz && rm jansson-2.10.tar.gz 
RUN cd /jansson-2.10 && ./configure && make && make install && cd 
.. && rm -rf jansson-2.10

#Install libcurl
RUN wget https://curl.haxx.se/download/curl-7.53.1.tar.gz && tar 
xf curl-7.53.1.tar.gz && rm curl-7.53.1.tar.gz
RUN cd curl-7.53.1 && ./configure && make && make install && cd .. 
 && rm -rf curl-7.53.1
RUN ln -s /usr/lib/x86_64-linux-gnu/libcurl-gnutls.so.4 
/usr/lib/libcurl.so && ldconfig

#Get my code
#TODO 
