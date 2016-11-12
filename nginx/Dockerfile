FROM debian:jessie-slim

RUN apt-get update && apt-get install -y nginx

ADD nginx.conf /etc/nginx/
ADD student.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/student.conf /etc/nginx/sites-enabled/student
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server phpfpm:9000; }" > /etc/nginx/conf.d/upstream.conf
RUN usermod -u 1000 www-data
CMD ["nginx"]
EXPOSE 80
EXPOSE 443
