FROM php:7.4.33-fpm-alpine

LABEL org.opencontainers.image.authors="dev@visualvoice.design"

RUN apk add --no-cache --update $PHPIZE_DEPS \
    # mysqli
	&& docker-php-ext-install mysqli \
    && docker-php-ext-enable mysqli \
    && echo "=============================================" \
    # xdebug
    && pecl install xdebug-2.8.0 \
    && docker-php-ext-enable xdebug \
	&& rm -rf /tmp/* /var/cache/apk/* \
    && echo "=============================================" \
    && php -m
    
# Create xdebug log
RUN touch /var/log/xdebug.log
# Allow xdebug to write to log
RUN chmod 777 /var/log/xdebug.log

# Work directory
WORKDIR /var/www