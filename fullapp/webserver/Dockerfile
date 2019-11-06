FROM nginx:latest

MAINTAINER cuong.ngo

RUN apt-get update && apt-get install -y vim

ADD webapp.conf /etc/nginx/conf.d/
ADD nginx.conf /etc/nginx/nginx.conf

RUN rm -rf /etc/nginx/conf.d/default.conf
RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80 443
