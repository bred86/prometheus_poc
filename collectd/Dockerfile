FROM ubuntu:trusty

MAINTAINER Matthias Endler (matthias.endler@trivago.com)

# Install required build tools
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive \
 && apt-get install -y collectd \
 && mkdir -p /usr/share/collectd/ /var/log/collectd/

COPY ./files/collectd.conf /etc/collectd.conf

CMD ["/usr/sbin/collectd", "-C", "/etc/collectd.conf", "-f"]
