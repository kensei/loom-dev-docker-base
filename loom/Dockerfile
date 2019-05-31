FROM node:8-stretch-slim

RUN echo "deb http://deb.debian.org/debian stretch main" > /etc/apt/sources.list \
 && echo "deb http://security.debian.org stretch/updates main" >> /etc/apt/sources.list \
 && curl -sL https://deb.nodesource.com/setup_8.x | bash \
 && apt-get update -qq \
 && apt-get install -y sudo procps git vim

RUN echo "%wheel ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers \
 && addgroup wheel \
 && usermod -aG wheel node

RUN curl -sL -o loom https://private.delegatecall.com/loom/linux/stable/loom \
 && chmod o+x loom \
 && ./loom version \
 && mv loom /usr/local/bin/loom \
 && loom init

USER node
WORKDIR /home/node

RUN git clone https://github.com/loomnetwork/vue-block-explorer.git \
 && yarn install

COPY ./genesis.json /home/node/chaindata/config/genesis.json

EXPOSE 46657

CMD ["loom", "run"]
