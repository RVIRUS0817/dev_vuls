FROM centos:7

RUN yum -y reinstall glibc-common
ENV LANG ja_JP.UTF-8

RUN yum -y install \
        vim \
        which \
        sqlite \
        git \
        gcc \
        make \
        wget \
        ;\
        yum clean all

RUN ln -sf /usr/share/zoneinfo/Japan /etc/localtime

RUN wget https://dl.google.com/go/go1.10.1.linux-amd64.tar.gz 
RUN sudo tar -C /usr/local -xzf go1.10.1.linux-amd64.tar.gz 
RUN rm -rf go1.10.1.linux-amd64.tar.gz 
RUN mkdir $HOME/go


CMD ["/bin/bash"]