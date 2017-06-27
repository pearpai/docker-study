FROM centos:latest

RUN yum -y update

RUN yum install -y  net-tools wget bind-utils iproute which make gcc

RUN yum clean all

CMD  /usr/sbin/init