FROM ubuntu:latest
MAINTAINER ["Manan Sankhla"]
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y supervisor \
openssh-server \
apache2 \
--no-install-recommends \
# python3.5 \
# python3-pip \
nginx \
default-jre \
&& \
apt-get clean \
&& \
rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/lock/apache2 /var/run/apache2 /var/run/sshd /var/log/supervisor
RUN mkdir -p /var/log/supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
EXPOSE 22 80 8081 
CMD ["/usr/bin/supervisord"]
