# VERSION 1.4.3
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-influxdb

FROM resin/armv7hf-debian:jessie
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV INFLUXDB_VERSION 1.4.3

# TODO: https://github.com/moby/moby/issues/33849
# ADD https://dl.influxdata.com/influxdb/releases/influxdb-${INFLUXDB_VERSION}_linux_armhf.tar.gz /influxdb.tar.gz
RUN apt update && \
    apt install curl
RUN curl https://dl.influxdata.com/influxdb/releases/influxdb-${INFLUXDB_VERSION}_linux_armhf.tar.gz -o /influxdb.tar.gz \ 
    && tar -xf /influxdb.tar.gz \
    && rm /influxdb.tar.gz \
    && cp /influxdb-${INFLUXDB_VERSION}-*/usr/bin/influx* /usr/bin/ \
    && mkdir /etc/influxdb \
    && mkdir /var/log/influxdb

EXPOSE     8086

VOLUME     [ "/etc/influxdb", "/var/lib/influxdb", ]

ENTRYPOINT [ "/usr/bin/influxd" ]

