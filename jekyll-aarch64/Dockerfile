
# base image
FROM arm64v8/ruby
MAINTAINER Peter <peter@minskio.co.uk>

# grab application, install dependencies in unused dir
RUN gem install jekyll bundler && jekyll new /bundle

# working directory
WORKDIR /srv/jekyll/

# run application
EXPOSE 4000
CMD ["jekyll","serve","--host","0.0.0.0"]
