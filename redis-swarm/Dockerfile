FROM centos:latest
RUN groupadd -r redis && useradd  -r -g redis redis
RUN  yum -y update &&  yum -y install epel-release \
&&   yum -y install redis  && yum -y install wget \
&&   yum -y install net-tools \
&&   yum -y install  ruby && yum  -y install  rubygems

# 下载ruby Redis管理工具 安装并删除安装包 版本最好对应
RUN wget https://rubygems.org/downloads/redis-3.2.1.gem  \
	&&  gem install -l ./redis-3.2.1.gem \
	&&  rm -f redis-3.2.1.gem

COPY  ./redis-trib.rb  /usr/bin
COPY  ./redis.sh       /usr/bin
RUN  mkdir -p /config && chmod  775  /usr/bin/redis.sh && chmod  775  /usr/bin/redis-trib.rb
COPY  ./redis.conf      /config




