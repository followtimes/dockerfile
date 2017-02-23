#build a image for buffalo web server

#xiaomi base image: centos 6.3 with base lib
FROM followtimes/centos:6.3
MAINTAINER followtimes <zhuhenghui@xiaomi.com>

#fix bash
#RUN cp /etc/skel/.* /root/ || echo "true"
#python version: 2.6.6

#prepare python env for buffalo
#ADD pip_requirements.txt /tmp
#WORKDIR /tmp
#RUN cat pip_requirements.txt | while read i ; do  $i  ; done
RUN pip install Flask==0.9
RUN pip install Flask-Admin==1.0.3
RUN pip install Flask-SQLAlchemy==0.16
RUN pip install Flask-WTF==0.8
RUN pip install Jinja2==2.6
RUN pip install MySQL-python==1.2.3
RUN pip install PyYAML==3.10
RUN pip install SQLAlchemy==0.7.9
RUN pip install WTForms==1.0.2
RUN pip install Werkzeug==0.8.3
RUN pip install argparse==1.2.1
RUN pip install httplib2==0.7.5
RUN pip install ipython==0.13.1
RUN pip install mock==1.0b1
RUN pip install networkx==1.7
RUN pip install ordereddict==1.1
#RUN pip install pika==0.9.6-pre5
#RUN pip install piped==0.5.0
#RUN pip install piped.contrib.zookeeper==0.5.0
RUN pip install pyOpenSSL==0.13
#RUN pip install python-ldap==2.4.10
RUN pip install python-memcached==1.48
RUN pip install thrift==0.8.0
RUN pip install txzookeeper==0.9.7
#RUN pip install uWSGI==1.2.6
RUN pip install zc-zookeeper-static==3.4.4
RUN pip install zc.thread==0.1.0
RUN pip install zc.zk==1.0.0
RUN pip install zope.interface==4.0.1
RUN pip install celery==3.1.23
RUN pip install celery-with-redis
RUN pip install msgpack-python
#RUN pip install xmlrpclib==1.0.1
RUN pip install misaka==1.0.2
RUN pip install pygments
RUN pip install sh
RUN pip install requests
RUN pip install gunicorn


#prepare env for hdfs sdk
ADD jdk1.6.0_37.tar.gz /opt/soft
ENV JAVA_HOME /opt/soft/jdk
ENV PATH $JAVA_HOME/bin:$PATH
ENV CLASSPATH $JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/rt.jar:$CLASSPATH

#prepare env for kerberos
RUN yum -y install krb5-devel krb5-libs  krb5-workstation

#do kinit cron
ADD krb5.conf /etc/
RUN yum install -y crontabs.noarch
ADD crontabfile /tmp/crontabfile
WORKDIR /tmp
RUN crontab crontabfile /etc/crontab


EXPOSE 5801

WORKDIR /home/work/buffalo

#start postfix server
RUN echo "/etc/init.d/postfix start" > /etc/rc.local

ENTRYPOINT ["gunicorn", "-c", "gunicorn.conf", "app:app", "-t", "6000"]
CMD ["--error-logfile", "/home/work/buffalo/log/app.log", "--log-level", "info"]
