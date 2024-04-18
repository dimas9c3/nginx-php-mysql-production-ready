FROM nginx:alpine

EXPOSE 80 443

RUN apk add --no-cache certbot \
    && echo "0 0,12 * * * python -c 'import random; import time; time.sleep(random.random() * 3600)' && certbot renew --post-hook \"nginx -s reload\"" > /etc/crontabs/root

CMD ["/bin/sh", "-c", "crond -b && certbot renew && nginx -g 'daemon off;'"]

# To create a letsencrypt cert, you need login the container,
# and execute the following command (don't forget config the nginx root folder, for here is /var/www/html):
# certbot certonly --webroot -w /var/www/html -d example.com -m example@example.com --agree-tos --noninteractive
# This docker image will try to renew all certs every 12h.
# Certs should be at /etc/letsencrypt/live/example.com/fullchain.pem and /etc/letsencrypt/live/example.com/key.pem respectively.
# You need set the nginx config to enable certs manually.