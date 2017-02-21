FROM codespaces/base-ubuntu-akurath:v0.1.0

MAINTAINER Vijayboopathy E <vibe@initcron.org>

RUN wget -qO- https://get.docker.com/ | sh && \
    curl -L "https://github.com/docker/compose/releases/download/1.10.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

EXPOSE 22 8000

CMD /usr/bin/akurath run
