FROM nginx

WORKDIR /var/www/html

ADD ./nginx.conf /etc/nginx/nginx.conf
ADD ./fast_cgi.conf /etc/nginx/conf.d/default.template

RUN cat /etc/nginx/conf.d/default.template | envsubst '$$COMPOSE_PROJECT_NAME' > /etc/nginx/conf.d/default.conf \
 && rm /etc/nginx/conf.d/default.template

CMD ["nginx", "-g", "daemon off;"]
