
# base image
FROM arm64v8/python
MAINTAINER Peter <peter@minskio.co.uk>

# grab application
RUN pip install flexget
RUN pip install transmissionrpc

# run application
CMD ["flexget","-c","/config/config.yml","daemon","start"]
