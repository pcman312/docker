FROM centos:centos7
MAINTAINER pcman312 <pcman312@gmail.com>
RUN cd /tmp
RUN curl -LO http://storage.googleapis.com/golang/go1.7.1.linux-amd64.tar.gz
RUN tar -C /usr/local -xvzf go1.7.1.linux-amd64.tar.gz
ENV PATH="/usr/local/go/bin/:${PATH}"
