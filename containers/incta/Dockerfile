FROM debian:latest
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN apt update && apt-get upgrade -y && apt-get install -y \
    ca-certificates \
    curl \
    gnupg
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --batch --yes --dearmor -o /etc/apt/keyrings/docker.gpg
RUN chmod a+r /etc/apt/keyrings/docker.gpg

RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update
RUN apt-get install -y \
    docker-ce \
    docker-ce-cli \
    containerd.io \
    docker-buildx-plugin \
    docker-compose-plugin

RUN apt-get install -y \
    libpq-dev \
    htop \
    systemctl \
    zip \
    libssl-dev \
    wget \
    git \
    procps \
    dirmngr \
    telnet \
    nano \
    net-tools

ENV NVM_DIR /tmp
ENV NODE_VERSION 21.7.2
RUN curl --silent -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash \
  && . $NVM_DIR/nvm.sh \
  && nvm install $NODE_VERSION \
  && nvm alias default $NODE_VERSION \
  && nvm use default

RUN ln -s /$NVM_DIR/versions/node/$NODE_VERSION/bin/node /usr/bin/node
ENV NODE_ENV development


##docker-compose build --pull --no-cache

##
##docker builder prune
## docker builder prune -a
