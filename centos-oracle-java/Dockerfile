
FROM centos:latest

LABEL maintainer="George T. C. Lai (tsungchih.hd@gmail.com)" \
      Description="CentOS + Oracle Java"

ARG VERSION=8
ARG UPDATE=121
ARG BUILD=b13
ARG CODE=e9e7ea248e2c4826b92b3f075a80e441

RUN yum update -y && \
    yum install -y wget && \
    wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/"$VERSION"u"$UPDATE"-"$BUILD"/"$CODE"/jdk-"$VERSION"u"$UPDATE"-linux-x64.rpm && \
    rpm -i jdk-"$VERSION"u"$UPDATE"-linux-x64.rpm && \
    alternatives --install /usr/bin/java java /usr/java/jdk1."$VERSION".0_"$UPDATE"/bin/java 1 && \
    alternatives --set java /usr/java/jdk1."$VERSION".0_"$UPDATE"/bin/java && \
    rm -rf jdk-$VERSIONu$UPDATE && \
    yum clean all

ENV JAVA_HOME /usr/java/jdk1."$VERSION".0_"$UPDATE"
