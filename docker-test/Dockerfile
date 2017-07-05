#Feature-1
#This is a test docker file
FROM ubuntu:14.04
MAINTAINER Docker Education Team <education@docker.com>
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y -q python-all python-pip 

RUN apt-get install -y python-pip; pip install --upgrade pip; apt-get install -y vim telnet curl mlocate logrotate rsyslog cron tar openssl openssl-dev net-tools

# Set default environment variables.
ENV HOME /root

# Define working directory.
WORKDIR /root

# Allow triggerable events on the first time running
RUN touch /tmp/firsttimerunning

# Add Volumes and Set permissions
RUN mkdir -p -m 777 /root/shared \
    && mkdir -p -m 777 /root \
    && mkdir -p -m 777 /root/containerfiles \
    && echo "alias vi='vim'" >> ~/.bashrc \
    && echo "alias tl='tail -f /var/log/nginx/*'" >> ~/.bashrc \
    && echo "alias el='tail -f /var/log/nginx/error.log'" >> ~/.bashrc \
    && echo "alias al='tail -f /var/log/nginx/access.log'" >> ~/.bashrc

# Add the starters and installers:
ADD ./containerfiles/ /root/containerfiles

RUN chmod 777 /root/containerfiles/*.sh

# Intalling the nginx 
RUN apt-get install -y nginx

# Adding the default file
RUN cp /root/containerfiles/index.html /usr/share/nginx/html

# Run/Compose ENV Variables:
ENV ENV_BASE_NGINX_CONFIG /root/containerfiles/base_nginx.conf
ENV ENV_DERIVED_NGINX_CONFIG /root/containerfiles/non_ssl.conf
ENV ENV_DEFAULT_ROOT_VOLUME /opt/web

# Port
EXPOSE 80 443

CMD ["/root/containerfiles/start-container.sh"]
