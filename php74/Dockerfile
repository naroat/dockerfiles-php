# 基础镜像
FROM php:7.4-fpm
# 维护人员
MAINTAINER taoran<taoran0796@163.com>
# 设置当前工作目录
WORKDIR /usr/share/nginx/html
# 拷贝当前目录的文件到镜像中
COPY . .
# 执行命令
RUN  mv /etc/apt/sources.list /etc/apt/sources.list.bak && cp sources.list /etc/apt \
        && apt-get update && apt-get install -y libpng-dev zlib1g-dev libmagickwand-dev libxslt-dev libzip-dev \
        && docker-php-ext-install -j$(nproc) pdo_mysql mysqli opcache sockets gd bcmath gettext xsl calendar pcntl shmop sysvmsg sysvsem sysvshm soap zip \
        # imagick
        && pecl install imagick \
        # redis
        && pecl install redis \
        # xlswriter
        && pecl install xlswriter \
        # swoole4.4
        && pecl install swoole-4.4.18 \
        # && pecl install redis-5.1.1.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini \
        # 开启扩展
        && docker-php-ext-enable xlswriter imagick redis swoole \
