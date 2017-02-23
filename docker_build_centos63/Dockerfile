#build a image for buffalo web server

#centos 6.3 with nothing
FROM gpmidi/centos-6.3
MAINTAINER followtimes <zhuhenghui@xiaomi.com>

#fix bash
RUN cp /etc/skel/.* /root/ || echo "true"

#update change repo to xiaomi repo
#RUN rm -rf /etc/yum.repos.d/*
#ADD CentOS-Base.repo /etc/yum.repos.d/entOS-Base.repo
#ADD epel.repo /etc/yum.repos.d/epel.repo

#yum install some base tool
RUN yum install -y wget unzip tar 

#yum install base devel 
#it's no useful to install python env only
#RUN yum install -y zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel expat-devel
RUN yum -y install gcc
#RUN yum -y install gcc-devel
RUN yum -y install python-devel
RUN yum -y install mysql-devel 

#for python devel python-ldap==2.4.10
#RUN yum -y install openldap-devel

#install setuptools devel
RUN yum install -y python-setuptools

#install pip 9.0.1
#ADD gzip to dir with extract
ADD pip-9.0.1.tar.gz /tmp/
WORKDIR /tmp/pip-9.0.1
RUN python setup.py install
