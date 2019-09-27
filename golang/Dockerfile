FROM golang:1.13-stretch
MAINTAINER wppurking 

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
ADD https://gist.githubusercontent.com/wppurking/2c26fccbc29add6d8310e352a2012983/raw/84cad45510710ead78e0f4ce38073f24c9d77db4/gistfile1.txt /etc/apt/sources.list
RUN apt-get update \
  && apt-get install ca-certificates vim -y

# install migration global package
RUN go get bitbucket.org/liamstask/goose/cmd/goose
# install packr for static file pack
RUN go get github.com/gobuffalo/packr/v2/packr2

ENV PATH /nodejs/bin:$PATH
RUN mkdir /nodejs && curl -s https://nodejs.org/dist/v10.15.3/node-v10.15.3-linux-x64.tar.gz | tar xvzf - -C /nodejs --strip-components=1 \
  && npm i -g yarn \
  && yarn config set registry https://registry.npm.taobao.org --global

ENV GO111MODULE=on
ENV GOPROXY=https://goproxy.cn
ENV ENVIROMENT=production
