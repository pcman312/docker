FROM centos:centos7
MAINTAINER pcman312 <pcman312@gmail.com>

RUN cd /tmp/

# Get golang
RUN curl -LO http://storage.googleapis.com/golang/go1.7.1.linux-amd64.tar.gz
RUN tar -C /usr/local -xvzf go1.7.1.linux-amd64.tar.gz
ENV PATH="/usr/local/go/bin/:${PATH}"

# Install prereqs for zeromq
RUN yum install libtool gcc gcc-c++ make -y

# Install zeromq
RUN cd /opt/
RUN curl -LO https://github.com/zeromq/zeromq4-1/releases/download/v4.1.5/zeromq-4.1.5.tar.gz
RUN cd zeromq-4.1.5
RUN ./autogen.sh
RUN ./configure
RUN make
#RUN make check
RUN make install
RUN echo /usr/local/lib > /etc/ld.so.conf.d/local.conf
RUN ldconfig
