
FROM centos:latest

LABEL maintainer="George T. C. Lai (tsungchih.hd@gmail.com)" \
      description="CentOS + OpenJDK"

ARG JAVA_VERSION=8

RUN yum update -y && \
    yum install -y java-1."$JAVA_VERSION".0-openjdk && \
    yum clean all

ENV JAVA_HOME /usr
