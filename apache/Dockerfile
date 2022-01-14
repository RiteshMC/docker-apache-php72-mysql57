FROM php:7.2-apache
WORKDIR /var/www/html/

RUN apt-get update

RUN apt install -y git zip unzip

RUN apt-get update -y && apt-get install -y libpng-dev zlib1g-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql mbstring gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

COPY my-apache-site.conf /etc/apache2/sites-available/my-apache-site.conf

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf &&\
    a2enmod rewrite &&\
    a2dissite 000-default &&\
    a2ensite my-apache-site &&\
    service apache2 restart


EXPOSE 80