FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && \
    apt-get install -y supervisor && \
    apt-get clean

ADD ./pkg /tmp/pkg
RUN dpkg -i /tmp/pkg/influxdb_0.8.8_amd64.deb && rm -r /tmp/pkg

ADD ./pkg/run-influxdb /usr/local/bin/run-influxdb

ADD ./cfg/influxdb.conf /etc/supervisor/conf.d/influxdb.conf

VOLUME /opt/influxdb/shared/data
VOLUME /var/log/supervisor

EXPOSE 8083
EXPOSE 8084
EXPOSE 8086

ENTRYPOINT /usr/bin/supervisord
