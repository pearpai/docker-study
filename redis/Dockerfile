FROM centos:base

RUN yum install -y ruby ruby-devel rubygems rpm-build

RUN gem install redis

ENV REDIS_VERSION="3.2.9"

RUN  wget http://download.redis.io/releases/redis-${REDIS_VERSION}.tar.gz -O /opt/redis-${REDIS_VERSION}.tar.gz

RUN tar vxf /opt/redis-${REDIS_VERSION}.tar.gz -C /opt

RUN ln -s /opt/redis-${REDIS_VERSION} /opt/redis

RUN cd /opt/redis && make distclean && make install

RUN cp /opt/redis/src/redis-trib.rb /usr/local/bin/

RUN echo 'vm.overcommit_memory = 1' >> /etc/sysctl.conf

RUN echo 'net.core.somaxconn = 1024' >> /etc/sysctl.conf

RUN echo never /sys/kernel/mm/transparent_hugepage/enabled

ADD startRedis.sh /usr/bin/startRedis.sh

ADD redis.conf /etc/redis.conf

RUN chmod +x /usr/bin/startRedis.sh

CMD  /usr/bin/startRedis.sh
