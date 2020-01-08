FROM debian

RUN apt-get update && apt-get install -y \
		ca-certificates \
		curl \
		openssh-server
RUN curl -Ss https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install -y gitlab-ce

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && /bin/bash
