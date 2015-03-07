FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && \
    apt-get install -y supervisor && \
    apt-get clean

ADD ./pkg/influxdb_0.8.8_amd64.deb /tmp/pkg/influxdb_0.8.8_amd64.deb
RUN dpkg -i /tmp/pkg/influxdb_0.8.8_amd64.deb && rm -r /tmp/pkg/influxdb_0.8.8_amd64.deb

ADD ./pkg/run-influxdb /usr/local/bin/run-influxdb

ADD ./cfg/supervisor.conf /etc/supervisor/conf.d/influxdb.conf

VOLUME /opt/influxdb/shared/data
VOLUME /var/log/supervisor

EXPOSE 8083
EXPOSE 8084
EXPOSE 8086

ENTRYPOINT /usr/bin/supervisord
