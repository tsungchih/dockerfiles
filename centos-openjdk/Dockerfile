#
# Author: George T. C. Lai
#
# sudo docker build --build-arg JAVA_VERSION={8 | 7} --build-arg JAVA_ENVIRONMENT={JDK | JRE | DEV} -t george/centos-openjdk .
#

FROM centos:latest

LABEL maintainer="George T. C. Lai (tsungchih.hd@gmail.com)" \
      description="CentOS + OpenJDK"

ARG JAVA_VERSION=8
ARG JAVA_ENVIRONMENT=JDK

ENV JAVA_HOME /usr

RUN yum update -y && \
    JAVA_PACKAGE="java-1.$JAVA_VERSION.0-openjdk"; \
    if [ "$JAVA_ENVIRONMENT" = "DEV" ]; then \
        JAVA_PACKAGE="$JAVA_PACKAGE-devel"; \
    elif [ "$JAVA_ENVIRONMENT" = "JRE" ]; then \
        JAVA_PACKAGE="$JAVA_PACKAGE-headless"; \
    fi; \
    yum install -y "$JAVA_PACKAGE" && \
    yum clean all

