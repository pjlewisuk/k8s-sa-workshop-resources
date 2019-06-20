FROM ubuntu:16.04

# Install dependencies
RUN apt-get update -y
RUN apt-get install -y git curl apache2 php7.0 libapache2-mod-php7.0 php7.0-mcrypt php7.0-mysql

# Install app
RUN rm -rf /var/www/html/*
ADD src /var/www/html

# Configure apache
RUN a2enmod rewrite
RUN chown -R www-data:www-data /var/www
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE  /var/run/apache2/apache2.pid
ENV APACHE_RUN_DIR   /var/run/apache2
ENV APACHE_LOCK_DIR  /var/lock/apache2
ENV APACHE_LOG_DIR   /var/log/apache2
ENV APACHE_DOCUMENT_ROOT   /var/www

RUN mkdir -p $APACHE_RUN_DIR
RUN mkdir -p $APACHE_LOCK_DIR
RUN mkdir -p $APACHE_LOG_DIR

EXPOSE 80

CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]
