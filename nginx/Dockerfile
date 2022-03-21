FROM nginx:latest

RUN addgroup --system --gid 1000 produpress
RUN adduser --system --uid 1000 --gid 1000 produpress

COPY sites.conf /etc/nginx/conf.d/default.conf

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    ca-certificates \
    ssl-cert

RUN touch /var/run/nginx.pid \
 && chown -Rf produpress:produpress \
    /var/run/nginx.pid \
    /var/cache/nginx \
    /var/log/nginx \
    /etc/ssl/private/ssl-cert-snakeoil.key
