###BACnet openstack image
###v0.8.3

from ubuntu:latest

#Dependencies
RUN apt-get update
RUN apt-get install -y wget git subversion
RUN apt-get install -y make gcc

#Get and compile bacnet-stack
RUN svn -q checkout https://svn.code.sf.net/p/bacnet/code/tags/bacnet-stack-0.8.3/ bacnet-stack
RUN cd bacnet-stack && make clean all -s
