
# base image
FROM arm64v8/debian
MAINTAINER Peter <peter@minskio.co.uk>

# prepare environment
RUN apt-get update
RUN apt-get install -y curl fuse man-db unzip

# always install latest version
RUN curl https://rclone.org/install.sh | bash

# config files
VOLUME ["/config"]

# port for serve
EXPOSE 8080

# execute
ENTRYPOINT ["/usr/bin/rclone"]
CMD ["--version"]
