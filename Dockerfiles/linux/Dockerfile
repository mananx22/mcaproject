FROM ubuntu:focal

MAINTAINER ["Manan Sankhla"]
ARG DEBIAN_FRONTEND=noninteractive
USER root

RUN apt-get update
RUN apt-get clean

RUN apt-get install -y \
supervisor \
apache2 \
openssh-server \
nginx \
openjdk-8-jdk \
default-jre \
--no-install-recommends \
&& apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/lock/apache2 /var/run/apache2 /var/run/sshd /var/log/supervisor
COPY ./nginx.conf /usr/share/nginx/
COPY ./supervisord.conf /etc/supervisor/conf.d/
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
CMD service supervisor restart && service apache2 restart && nginx -c /usr/share/nginx/nginx.conf && /usr/bin/supervisord 
EXPOSE 22 80 8080

