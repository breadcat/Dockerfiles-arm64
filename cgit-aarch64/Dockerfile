
# base image
FROM arm64v8/nginx
MAINTAINER Peter <peter@minskio.co.uk>

# update repos and install application
RUN apt-get update && apt-get install -y cgit fcgiwrap nginx

# configure cgit and nginx
RUN echo "scan-path=/git" >> /etc/cgitrc
RUN echo "virtual-root=/" >> /etc/cgitrc
RUN echo "css=/cgit.css" >> /etc/cgitrc
RUN echo "logo=/cgit.png" >> /etc/cgitrc
COPY nginx.conf /etc/nginx/nginx.conf

# service starter
RUN echo "#!/bin/bash" > /start.sh
RUN echo "/etc/init.d/fcgiwrap start" >> /start.sh
RUN echo "/etc/init.d/nginx start" >> /start.sh
RUN echo "while true; do sleep 1d; done" >> /start.sh
RUN chmod +x /start.sh

# run application
EXPOSE 80
CMD /start.sh
