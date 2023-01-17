#FROM nginx:latest
#FROM library/nginx:latest
FROM docker.io/library/nginx:latest
RUN rm /etc/nginx/conf.d/*
ENV MY_VAR "default"
ADD hello.conf.template /etc/nginx/templates/
ADD index.html /usr/share/nginx/html/