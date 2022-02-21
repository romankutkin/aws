FROM php:8.1-fpm-alpine

RUN apk add --no-cache \
		acl \
	;

# COMPOSER
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

# ENTRYPOINT
COPY docker/php-fpm/docker-entrypoint.sh /usr/local/bin/docker-entrypoint
RUN chmod +x /usr/local/bin/docker-entrypoint

WORKDIR /usr/share/nginx/html

COPY . .

RUN mkdir -p var/cache var/log

VOLUME /usr/share/nginx/html/var

ENTRYPOINT ["docker-entrypoint"]
CMD ["php-fpm"]
