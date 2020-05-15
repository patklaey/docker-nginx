FROM nginx
LABEL maintainer="pat@247.ch"

RUN sed -i "17i\\    server_names_hash_bucket_size 64;" /etc/nginx/nginx.conf

COPY conf.d/. /etc/nginx/conf.d/

