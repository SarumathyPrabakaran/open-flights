
FROM ruby


WORKDIR /home/app
RUN gem install rails bundler
RUN gem install rails
RUN apt-get update -qq && apt-get install -y nodejs

COPY  Gemfile ./Gemfile 
COPY Gemfile.lock ./Gemfile.lock 

RUN gem install bundler:2.3.6
RUN bundle install
RUN apt install npm -y
RUN npm install -g yarn -y
COPY . .
# RUN bundle exec rails webpacker:install
RUN yarn install
RUN yarn

EXPOSE 3000

RUN ./bin/webpack-dev-server &

CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0" ]
