########################################################################################################################
# Docker build command:
# docker build -t busybox .
# Docker run command:
# docker run -it busybox
########################################################################################################################

FROM registry.access.redhat.com/ubi7/ubi:latest

MAINTAINER "Amol Patil <amol.patil2@.ibm.com>"

RUN yum update -y \
    && yum install -y make git wget gcc zip bzip2 

RUN wget https://busybox.net/downloads/busybox-1.30.1.tar.bz2 \
    && tar -xvjf busybox-1.30.1.tar.bz2 \
    && rm busybox-1.30.1.tar.bz2 

RUN cd busybox-1.30.1 && make defconfig && make && make install \
    && yum remove -y make wget git gcc zip bzip2 && yum -y autoremove

RUN ln -s /busybox-1.30.1/busybox /usr/local/bin/busybox 

ENTRYPOINT ["/bin/bash"]



