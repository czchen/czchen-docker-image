FROM	ubuntu:14.04

ENV	DEBIAN_FRONTEND noninteractive

RUN	apt-get update -y && \
	apt-get install -y supervisor && \
	apt-get clean

ADD	./pkg /tmp/pkg
RUN	dpkg -i /tmp/pkg/influxdb_0.8.8_amd64.deb
RUN	/tmp/pkg/run-influxdb /usr/local/bin/run-influxdb

VOLUME	/opt/influxdb/shared/data

EXPOSE	8083
EXPOSE	8084
EXPOSE	8086

ENTRYPOINT	/usr/bin/supervisord
