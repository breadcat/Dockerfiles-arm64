
# base image
FROM arm64v8/python
MAINTAINER Peter <peter@minskio.co.uk>

# docker run -it -p 8090:80 arm64v8/python bash
# https://github.com/the-paperless-project/paperless

# variables
ENV EXPORT_DIR=/export
ENV CONSUMPTION_DIR=/consume

# update repos and install dependencies
RUN apt-get update
RUN apt-get install -y git tesseract-ocr tesseract-ocr-eng imagemagick optipng unpaper libpoppler-cpp-dev ghostscript gnupg
RUN git clone https://github.com/the-paperless-project/paperless /usr/src/paperless
RUN pip install --user --requirement /usr/src/paperless/requirements.txt

# expose ports

VOLUME ["/usr/src/paperless/data", "/usr/src/paperless/media", "/consume", "/export"]

EXPOSE 8000

# run command
WORKDIR /usr/src/paperless
ENTRYPOINT ["python3", "src/manage.py"]
CMD ["--help"]
