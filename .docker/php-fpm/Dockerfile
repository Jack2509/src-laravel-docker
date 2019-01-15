FROM 7.1-alpine3.8


# copy PHP configuration to image
COPY ./usr/local/etc/php/ /usr/local/etc/php/

# add required php extensions
RUN apk --no-cache update \
    && apk --no-cache upgrade \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install pdo pdo_mysql zip \
    && rm -rf /var/cache/apk/* /tmp/*

# copy source code and config to image
COPY ./../../src /var/www/html

# copy start script to image
COPY ./start /start

# run start script on container startup
CMD ["/start"]