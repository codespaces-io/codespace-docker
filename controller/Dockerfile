FROM ubuntu:14.04
MAINTAINER Babu R <babu@initcron.org>

WORKDIR /workspace
VOLUME /workspace

RUN apt-get update && \
	apt-get install -y make g++ python git curl wget openssh-server sudo vim libdevmapper-dev && \
	curl -sL https://deb.nodesource.com/setup | sudo bash - && \
	apt-get install -y nodejs && \
	npm -g install node-gyp akurath && \
	cd /usr/lib/node_modules/akurath/node_modules/shux/node_modules/pty.js && \
	make clean && \
	make

RUN mkdir /var/run/sshd && \
    wget -qO- https://get.docker.com/ | sh && \
    curl -L "https://github.com/docker/compose/releases/download/1.10.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

COPY motd.sh /opt/

RUN chmod +x /opt/motd.sh && \
    sh /opt/motd.sh && \
    rm -rf motd.sh

RUN useradd -ms /bin/bash devops && \
    echo 'devops:codespaces' |chpasswd && \
    adduser devops sudo && \
    echo 'devops ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

EXPOSE 22 8000

CMD /usr/bin/akurath run
