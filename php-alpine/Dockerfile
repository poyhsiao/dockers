# Use Alpine Linux
FROM alpine:edge

# Maintaniner
MAINTAINER Kim Hsiao <white.shopping@gmail.com>


# Environments
# timezone environment
ENV TIMEZONE    Asia/Taipei

# php setting memory
ENV PHP_MEMORY_LIMIT    512M
ENV MAX_UPLOAD  64M
ENV PHP_MAX_FILE_UPLOAD 50
ENV PHP_MAX_POST    100M

# opcache environment
ENV CACHE_DIR   /tmp
ENV MEMORY_CONSUMPTION  128
ENV STRING_BUFFER   8
ENV ACCELERATED_FILES   4000
ENV REVALIDATE_FREQ 60
ENV FAST_SHUTDOWN   1


# Starting settings
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories && \
    apk update && \
    apk upgrade && \
    apk add --update tzdata && \
    cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
    echo "${TIMEZONE}" > /etc/timezone && \
    apk add --update \
        php7-intl \
        php7-openssl \
        php7-sqlite3 \
        php7-pear \
        php7-litespeed \
        php7-gmp \
        php7-pdo_mysql \
        php7-pcntl \
        php7-oauth \
        php7-xsl \
        php7-fpm \
        php7-gmagick \
        php7-mysqlnd \
        php7-enchant \
        php7-solr \
        php7-uuid \
        php7-pspell \
        php7-ast \
        php7-redis \
        php7-snmp \
        php7-mbstring \
        php7-lzf \
        php7-timezonedb \
        php7-xmlrpc \
        php7-stats \
        php7-xmlreader \
        php7-pdo_sqlite \
        php7-exif \
        php7-msgpack \
        php7-opcache \
        php7-ldap \
        php7-posix \
        php7-session \
        php7-gd \
        php7-gettext \
        php7-mailparse \
        php7-json \
        php7-xml \
        php7-mongodb \
        php7-iconv \
        php7-sysvshm \
        php7-curl \
        php7-shmop \
        php7-phar \
        php7-pdo_pgsql \
        php7-imap \
        php7-pdo_dblib \
        php7-pgsql \
        php7-zip \
        php7-ctype \
        php7-inotify \
        php7-amqp \
        php7-mcrypt \
        php7-readline \
        php7-wddx \
        php7-libsodium \
        php7-bcmath \
        php7-calendar \
        php7-tidy \
        php7-dom \
        php7-sockets \
        php7-zmq \
        php7-memcached \
        php7-soap \
        php7-sysvmsg \
        php7-zlib \
        php7-ssh2 \
        php7-ftp \
        php7-sysvsem \
        php7-pdo \
        php7-bz2 \
        php7-mysqli && \

    # Set php environment
    sed -i "s|;*daemonize\s*=\s*yes|daemonize = no|g" /etc/php7/php-fpm.conf && \
    sed -i "s|;*listen\s*=\s*127.0.0.1:9000|listen = 9000|g" /etc/php7/php-fpm.d/www.conf && \
    sed -i "s|;*listen\s*=\s*/||g" /etc/php7/php-fpm.d/www.conf && \
    sed -i "s|;*date.timezone =.*|date.timezone = ${TIMEZONE}|i" /etc/php7/php.ini && \
    sed -i "s|;*memory_limit =.*|memory_limit = ${PHP_MEMORY_LIMIT}|i" /etc/php7/php.ini && \
    sed -i "s|;*upload_max_filesize =.*|upload_max_filesize = ${MAX_UPLOAD}|i" /etc/php7/php.ini && \
    sed -i "s|;*max_file_uploads =.*|max_file_uploads = ${PHP_MAX_FILE_UPLOAD}|i" /etc/php7/php.ini && \
    sed -i "s|;*post_max_size =.*|post_max_size = ${PHP_MAX_POST}|i" /etc/php7/php.ini && \
    sed -i "s|;*cgi.fix_pathinfo=.*|cgi.fix_pathinfo= 0|i" /etc/php7/php.ini && \

    # enable php opcache
    echo "opcache.enable=1" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.enable_cli=1" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.file_cache=${CACHE_DIR}" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.memory_consumption=${MEMORY_CONSUMPTION}" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.interned_strings_buffer=${STRING_BUFFER}" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.max_accelerated_files=${ACCELERATED_FILES}" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.revalidate_freq=${REVALIDATE_FREQ}" >> /etc/php7/conf.d/00_opcache.ini && \
    echo "opcache.fast_shutdown=${FAST_SHUTDOWN}" >> /etc/php7/conf.d/00_opcache.ini && \

    # clean up
    mkdir /www && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*

# Set work dir
WORKDIR /www

# Expose volumes
VOLUME ["/www"]

# Expose ports
EXPOSE 9000

# Entry point
ENTRYPOINT ["/usr/sbin/php-fpm7"]

