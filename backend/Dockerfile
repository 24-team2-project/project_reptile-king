# 베이스 이미지 설정
FROM php:8.3.2-fpm

# 작업 디렉토리 설정
WORKDIR /var/www

# 의존성 패키지 설치
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    libzip-dev \
    libonig-dev \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl

# PHP 확장 설치
RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
RUN docker-php-ext-configure gd --with-jpeg=/usr/include/ --with-freetype=/usr/include/
RUN docker-php-ext-install gd

# Composer 설치
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# 앱 소스를 도커 이미지에 복사
COPY . .

# Composer로 의존성 설치
RUN composer install

# 컨테이너 시작 시 포트 설정
EXPOSE 9000
CMD ["php-fpm"]