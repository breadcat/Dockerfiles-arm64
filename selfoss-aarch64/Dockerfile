
# base image
FROM arm64v8/php:apache
MAINTAINER Peter <peter@minskio.co.uk>

# version variable
ENV VER=2.18

# prepare environment
RUN apt-get update
RUN apt-get install -y nano unzip wget libpng-dev libpq-dev
RUN a2enmod headers rewrite
RUN docker-php-ext-install gd mbstring pdo_pgsql pdo_mysql

# grab and unpack application
WORKDIR /var/www/html/
RUN wget https://github.com/SSilence/selfoss/releases/download/$VER/selfoss-$VER.zip
RUN unzip "selfoss-$VER.zip" && rm "selfoss-$VER.zip"

# config file
RUN chmod 0777 /var/www/html/data/ -R
RUN ln -s data/config.ini defaults.ini

# cron entry for updates
# 0 * * * * curl "https://rss.minskio.co.uk/update" &

# run things
CMD "apache2-foreground"
