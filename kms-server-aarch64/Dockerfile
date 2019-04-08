
# base image
FROM arm64v8/python
MAINTAINER Peter <peter@minskio.co.uk>

# update, install, clone repo
RUN apt-get update
RUN apt-get install -y git python
RUN git clone https://github.com/SourceDoctor/py-kms.git

# expose ports
EXPOSE 1688/tcp

# run command
CMD ["python2", "py-kms/server.py"]
