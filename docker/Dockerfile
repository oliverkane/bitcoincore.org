FROM ruby:2.5.5 as build

WORKDIR /app/src
COPY . .
RUN gem update --system
RUN gem install bundler
RUN bundle install
RUN bundle exec jekyll build 

FROM nginx:stable-alpine as host
COPY --from=0 /app/src/_site /usr/share/nginx/html

ADD docker/nginx.conf /etc/nginx/nginx.conf