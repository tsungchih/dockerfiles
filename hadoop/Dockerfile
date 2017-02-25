#
# Author: George T. C. Lai (tsungchih.hd@gmail.com)
#
#

FROM george/centos-openjdk:8_jre

ARG HADOOP_VERSION=2.7.2

LABEL Maintainer="George T. C. Lai (tsungchih.hd@gmail.com)" \
      Description="Hadoop" \
      "Hadoop Version"="$HADOOP_VERSION"

ENV HADOOP_HOME=/usr/local/hadoop \
    HADOOP_PID_DIR=/var/run \
    HADOOP_LOG_DIR=/var/log

WORKDIR /root

RUN yum update -y && \
    yum install -y openssh-server openssh-clients wget tar which hostname && \
    wget -t 100 --retry-connrefused -O hadoop-${HADOOP_VERSION}.tar.gz "http://www.apache.org/dyn/closer.lua?filename=hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz&action=download" && \
    tar xzf hadoop-${HADOOP_VERSION}.tar.gz && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -q -N "" -t rsa -f /root/.ssh/id_rsa && \
    cp /root/.ssh/id_rsa.pub /root/.ssh/authorized_keys && \
    ln -s /root/hadoop-${HADOOP_VERSION} /usr/local/hadoop && \
    yum remove -y wget tar && \
    yum autoremove -y && \
    yum clean all

COPY conf/core-site.xml /root/hadoop/etc/hadoop/
COPY conf/hdfs-site.xml /root/hadoop/etc/hadoop/
COPY conf/mapred-site.xml /root/hadoop/etc/hadoop/
COPY conf/yarn-site.xml /root/hadoop/etc/hadoop/
COPY profile.d/hadoop.sh /etc/profile.d

EXPOSE 8020 8042 8088 9000 10020 19888 50010 50020 50070 50075 50090
