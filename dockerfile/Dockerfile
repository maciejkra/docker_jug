FROM debian

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends apache2 php5 php5-mysql mysql-server && \
    apt-get clean && \
    a2enmod rewrite && \
    rm -R /var/www/html/*

ADD https://wordpress.org/wordpress-4.6.1.tar.gz /

RUN tar zxfp /*.tar.gz -C /var/www/html/ --strip 1 && \
    chown -R www-data:www-data /var/www/html/ && \
    rm /*.tar.gz

EXPOSE 80

CMD service mysql start && mysqladmin -u root password "pass" && mysql -u root -ppass -e "create database wordpress"  && /usr/sbin/apache2ctl -D FOREGROUND
