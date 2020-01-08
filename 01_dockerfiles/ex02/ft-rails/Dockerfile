FROM ruby

RUN apt-get update && apt-get install -y \
		build-essential \
		nodejs \
		sqlite3 \
	&& rm -rf /var/lib/apt/lists/*
RUN gem install rails bundler:1.16.6 activerecord-jdbcsqlite3-adapter

ONBUILD WORKDIR /opt/app
ONBUILD COPY app .
ONBUILD RUN bundle update && bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed
