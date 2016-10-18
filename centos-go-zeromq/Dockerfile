FROM centos:centos7
MAINTAINER pcman312 <pcman312@gmail.com>

WORKDIR /tmp/

# Install tools
RUN yum install wget openssh-clients rsync -y

# Install golang
RUN curl -LOs http://storage.googleapis.com/golang/go1.7.1.linux-amd64.tar.gz
RUN tar -C /usr/local -xzf go1.7.1.linux-amd64.tar.gz
ENV PATH="/usr/local/go/bin/:${PATH}"

# Install prereqs for zeromq
RUN yum install libtool gcc gcc-c++ make -y > /dev/null

# Install zeromq
WORKDIR /opt/
RUN curl -LOs https://github.com/zeromq/zeromq4-1/releases/download/v4.1.5/zeromq-4.1.5.tar.gz
RUN tar -xzf zeromq-4.1.5.tar.gz
WORKDIR /opt/zeromq-4.1.5
RUN ls -l
RUN ./autogen.sh
RUN ./configure
RUN make
#RUN make check
RUN make install
RUN echo /usr/local/lib > /etc/ld.so.conf.d/local.conf
RUN ldconfig
RUN cp ./src/libzmq.pc /usr/lib64/pkgconfig/

# Install fpm and rpmbuild
RUN yum install ruby ruby-devel rpm-build -y
RUN gem install fpm

# Install ansible
RUN curl -O http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
RUN rpm -ivh epel-release-7-8.noarch.rpm
RUN yum install ansible -y

# Install awscli
WORKDIR /tmp
RUN curl -O https://bootstrap.pypa.io/get-pip.py
RUN python2.7 get-pip.py
RUN pip install awscli

# Install jq
RUN wget http://stedolan.github.io/jq/download/linux64/jq
RUN chmod +x ./jq
RUN mv ./jq /usr/bin

# Set up .ssh folders
RUN mkdir -p /root/.ssh
RUN mkdir -p /root/.ssh/sockets
