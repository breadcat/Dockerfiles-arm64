
# base image
FROM arm64v8/nginx
MAINTAINER Peter <peter@minskio.co.uk>

# environment
ENV VER=0.4.6

# dependencies
RUN apt-get update
RUN apt-get install -y unzip wget sqlite3 php-sqlite3 php-mysql php-fpm php-mbstring php-xml

# grab application, install dependencies
RUN mkdir "/var/www/"
WORKDIR "/var/www"
RUN wget "https://github.com/sabre-io/Baikal/releases/download/$VER/baikal-$VER.zip"
RUN unzip "baikal-$VER.zip" && rm "baikal-$VER.zip"

# config file and permissions
COPY nginx.conf "/etc/nginx/nginx.conf"
RUN chmod 0777 "/var/www/baikal/Specific" -R

# service starter
RUN echo "#!/bin/bash" > /start.sh
RUN echo "/etc/init.d/nginx start" >> /start.sh
RUN echo "/etc/init.d/php7.0-fpm start" >> /start.sh
RUN echo "while true; do sleep 1d; done" >> /start.sh
RUN chmod +x /start.sh

# run application
EXPOSE 80
CMD /start.sh
