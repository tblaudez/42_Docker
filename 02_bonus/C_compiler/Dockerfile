FROM debian

RUN apt-get update && apt-get install -y \
		git \
		gcc \
		make \
		vim \
	&& rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY main.c /app
RUN gcc /app/main.c -o /app/main

ENTRYPOINT /app/main
