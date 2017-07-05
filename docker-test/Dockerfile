#Feature-1
#This is a test docker file
FROM ubuntu:14.04
MAINTAINER Docker Education Team <education@docker.com>
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y -q python-all python-pip 
RUN apt-get install apache2
RUN service apache2 start

EXPOSE 80
# End Nginx-PHP
