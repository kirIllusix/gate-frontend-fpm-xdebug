# gate-frontend-fpm-xdebug
```
FROM mrchub/gate-frontend-fpm:latest

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive
# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive

# Install the xdebug extension
RUN pecl install xdebug \
	&& docker-php-ext-enable xdebug

# Copy xdebug configration for remote debugging
COPY ./src/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

RUN apt-get autoremove -y \
	&& apt-get clean -y \
	&& rm -rf /tmp/* /var/tmp/* \
	&& find /var/cache/apt/archives /var/lib/apt/lists -not -name lock -type f -delete \
	&& find /var/cache -type f -delete
```
