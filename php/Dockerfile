FROM debian:bullseye-slim

RUN addgroup --system --gid 1000 produpress
RUN adduser --system --uid 1000 --gid 1000 produpress


RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    ca-certificates \
    apt-transport-https \
    software-properties-common \
    lsb-release \
    wget \
    curl

RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg

RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    php8.1-bcmath \
    php8.1-bz2 \
    php8.1-cli \
    php8.1-common \
    php8.1-curl \
    php8.1-fpm \
    php8.1-gd \
    php8.1-igbinary \
    php8.1-intl \
    php8.1-mbstring \
    php8.1-mysql \
    php8.1-opcache \
    php8.1-pcov \
    php8.1-readline \
    php8.1-redis \
    php8.1-soap \
    php8.1-sqlite3 \
    php8.1-xml \
    php8.1-zip \
    php-redis

COPY php-fpm.conf /etc/php/8.1/fpm/pool.d/www.conf

STOPSIGNAL SIGQUIT

EXPOSE 9000
CMD ["/usr/sbin/php-fpm8.1"]