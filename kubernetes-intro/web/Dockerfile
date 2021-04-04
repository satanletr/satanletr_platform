FROM nginx:latest
#RUN apt-get update && apt-get install -y htop
ARG nginx_uid=1001
ARG nginx_gid=1001
RUN usermod -u $nginx_uid -o nginx && groupmod -g $nginx_gid -o nginx
RUN mkdir -p /app
COPY ./index.html /app/homework.html
COPY ./default.conf /etc/nginx/conf.d/default.conf
WORKDIR /app
RUN chown -R nginx:nginx /app && chmod -R 755 /app && \
        chown -R nginx:nginx /var/cache/nginx && \
        chown -R nginx:nginx /var/log/nginx && \
        chown -R nginx:nginx /etc/nginx/conf.d
RUN touch /var/run/nginx.pid && \
        chown -R nginx:nginx /var/run/nginx.pid
EXPOSE 8000
USER nginx
