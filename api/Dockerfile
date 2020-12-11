FROM ruby:2.5.7

RUN apt-get update -qq
RUN apt-get install -y build-essential libpq-dev nodejs

RUN mkdir /api

WORKDIR /api

ADD Gemfile /api
ADD Gemfile.lock /api

RUN gem install bundler rake
RUN bundle install

ADD . /api

CMD ["rails", "server", "-b", "0.0.0.0"]

# FROM ruby:2.5.7
# RUN apt update
# RUN apt install -y build-essential libpq-dev nodejs postgresql postgresql-client
# RUN gem install bundler rake
# COPY . /home/Trabalho-Individual-2020-1/api/
# WORKDIR /home/Trabalho-Individual-2020-1/api/
# RUN bundle install
