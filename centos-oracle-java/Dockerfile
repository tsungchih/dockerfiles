#
# Author: George T. C. Lai (tsungchih.hd@gmail.com)
#
# Build Usage:
# sudo docker build -t george/centos-oracle-java \
#      --build-arg JAVA_MAJOR_VERSION=8 \
#      --build-arg JAVA_UPDATE_VERSION=121 \
#      --build-arg JAVA_BUILD_NUMBER=b13 \
#      --build-arg JAVA_SIGNATURE=e9e7ea248e2c4826b92b3f075a80e441
#      .
#

FROM centos:latest

LABEL maintainer="George T. C. Lai (tsungchih.hd@gmail.com)" \
      Description="CentOS + Oracle Java"

ARG JAVA_MAJOR_VERSION=8
ARG JAVA_UPDATE_VERSION=121
ARG JAVA_BUILD_NUMBER=b13
ARG JAVA_SIGNATURE=e9e7ea248e2c4826b92b3f075a80e441

ENV JAVA_VERSION=1.$JAVA_MAJOR_VERSION.0_$JAVA_UPDATE_VERSION \
    JAVA_HOME=/usr/java/jdk1.$JAVA_MAJOR_VERSION.0_$JAVA_UPDATE_VERSION

WORKDIR /root

RUN yum update -y && \
    yum install -y wget && \
    wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/"$JAVA_MAJOR_VERSION"u"$JAVA_UPDATE_VERSION"-"$JAVA_BUILD_NUMBER"/$JAVA_SIGNATURE/jdk-"$JAVA_MAJOR_VERSION"u"$JAVA_UPDATE_VERSION"-linux-x64.rpm && \
    rpm -i jdk-"$JAVA_MAJOR_VERSION"u"$JAVA_UPDATE_VERSION"-linux-x64.rpm && \
    alternatives --install /usr/bin/java java ${JAVA_HOME}/bin/java 1 && \
    alternatives --install /usr/bin/jps jps ${JAVA_HOME}/bin/jps 1 && \
    alternatives --set java ${JAVA_HOME}/bin/java && \
    alternatives --set jps ${JAVA_HOME}/bin/jps && \
    rm -rf jdk-"$JAVA_MAJOR_VERSION"u"$JAVA_UPDATE_VERSION"-linux-x64.rpm && \
    yum remove -y wget && \
    yum clean all

