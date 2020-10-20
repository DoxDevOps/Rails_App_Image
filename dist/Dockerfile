FROM ruby:2.5.3
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs libapache2-mod-php7.0
RUN mkdir /www
WORKDIR /www
ADD Gemfile /www/Gemfile
ADD Gemfile.lock /www/Gemfile.lock
RUN apt-get install -y curl patch gawk g++ gcc make libc6-dev patch libreadline6-dev zlib1g-dev libyaml-dev libsqlite3-dev sqlite3 autoconf libgdbm-dev libncurses5-dev automake libtool bison pkg-config libffi-$
RUN useradd -ms /bin/bash app
USER app
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RUN /bin/bash -l -c "curl -L get.rvm.io | bash -s stable --rails"
RUN /bin/bash -l -c "rvm install 2.5.3"
RUN /bin/bash -l -c "echo 'gem: --no-ri --no-rdoc' > ~/.gemrc"
RUN /bin/bash -l -c "gem install bundler"
RUN bundle install
ADD . /www

