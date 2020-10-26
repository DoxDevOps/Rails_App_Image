FROM ruby:2.5.3
RUN apt-get update -qq && apt-get install -y nodejs libmariadbclient-dev
RUN mkdir /www
WORKDIR /www
COPY Gemfile /www
RUN bundle install
COPY . /www

# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]

