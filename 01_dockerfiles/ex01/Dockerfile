FROM alpine as build
RUN wget https://files.teamspeak-services.com/releases/server/3.7.1/teamspeak3-server_linux_amd64-3.7.1.tar.bz2 \
	&& tar -xvf teamspeak3-server_linux_amd64-3.7.1.tar.bz2  \
	&& rm teamspeak3-server_linux_amd64-3.7.1.tar.bz2

FROM debian
ENV TS3SERVER_LICENSE=accept
EXPOSE 9987/udp
EXPOSE 10011
EXPOSE 30033
RUN apt-get update \
	&& apt-get install -y ca-certificates \
	&& rm -rf /var/lib/apt/lists/*
COPY --from=build /teamspeak3-server_linux_amd64 /teamspeak_server3
ENTRYPOINT sh /teamspeak_server3/ts3server_minimal_runscript.sh
