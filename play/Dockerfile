FROM ubuntu:18.04 AS build-stage

ENV JAVA_VERSION 11.0.5
ENV PLAY_VERSION 1.4.2

ADD http://devops.easya.cc/play-${PLAY_VERSION}.zip /opt
ADD http://devops.easya.cc/jdk-${JAVA_VERSION}_linux-x64_bin.tar.gz /opt

RUN set -x \
  && apt update \
  && apt install -qqy unzip \
  && cd /opt \
  && tar   xf jdk-${JAVA_VERSION}_linux-x64_bin.tar.gz \
  && unzip -q play-${PLAY_VERSION}.zip


FROM ubuntu:18.04

ENV JAVA_VERSION 11.0.5
ENV PLAY_VERSION 1.4.2

ENV JAVA_HOME /opt/jdk-${JAVA_VERSION}
ENV PLAY_HOME /opt/play-${PLAY_VERSION}

COPY --from=build-stage $JAVA_HOME $JAVA_HOME
COPY --from=build-stage $PLAY_HOME $PLAY_HOME

RUN set -x \
  && apt update \
  && apt install -qqy python \
  && rm -rf /var/lib/apt/lists/*
  
ENV CLASSPATH $JAVA_HOME/lib 
ENV PATH $PLAY_HOME:$JAVA_HOME/bin:$PATH 
