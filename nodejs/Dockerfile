FROM ubuntu:14.04

MAINTAINER Kim Hsiao

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y curl build-essential python && \
    apt-get clean

RUN curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash - && \
    apt-get update && \
    apt-get install -y nodejs

RUN npm install -g nodemon pm2 babel-cli

RUN mkdir -p /root/web


EXPOSE 8888

CMD ["/bin/bash"]
