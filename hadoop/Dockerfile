FROM centos:base

ADD jdk-8u131-linux-x64.rpm /opt/jdk-8u131-linux-x64.rpm

RUN rpm -ivh /opt/jdk-8u131-linux-x64.rpm

RUN mkdir /opt/hadoop/

RUN wget http://apache.forsale.plus/hadoop/common/hadoop-2.8.0/hadoop-2.8.0.tar.gz -O /opt/hadoop/hadoop-2.8.0.tar.gz

RUN tar vxf /opt/hadoop/hadoop-2.8.0.tar.gz -C /opt/hadoop/

RUN yum -y install openssh openssh-server openssh-clients

RUN echo "export JAVA_HOME=/usr/java/jdk1.8.0_131" >> /etc/profile

RUN echo "export  CLASSPATH=$:CLASSPATH:$JAVA_HOME/lib/" >> /etc/profile

RUN echo "export  PATH=$PATH:$JAVA_HOME/bin" >> /etc/profile

RUN source /etc/profile

RUN mkdir RUN touch /root/.ssh

RUN touch /root/.ssh/authorized_keys /root/.ssh/id_rsa /root/.ssh/id_rsa.pub

RUN chmod 400 /root/.ssh/authorized_keys /root/.ssh/id_rsa /root/.ssh/id_rsa.pub

RUN mkdir  /root/hadoop
#RUN mkdir  /root/hadoop/tmp
#RUN mkdir  /root/hadoop/var
#RUN mkdir  /root/hadoop/dfs
#RUN mkdir  /root/hadoop/dfs/name
#RUN mkdir  /root/hadoop/dfs/data