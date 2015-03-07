FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && \
    apt-get install -y nginx-light supervisor && \
    apt-get clean

ADD ./pkg/ /tmp/pkg
RUN mkdir -p /opt/grafana && \
    cd /opt/grafana && \
    tar xzf /tmp/pkg/grafana-1.9.1.tar.gz --strip-components=1 && \
    rm -r /tmp/pkg/grafana-1.9.1.tar.gz
ADD ./cfg/config.js /opt/grafana/config.js

ADD ./cfg/nginx.conf /etc/supervisor/conf.d/nginx.conf
VOLUME /var/log/supervisor

EXPOSE 80

ENTRYPOINT /usr/bin/supervisord
