FROM node:8-alpine

RUN apk add --update --no-cache alpine-sdk shadow python

RUN usermod -aG wheel node \
  && sed -i -e 's/# %wheel\sALL=(ALL)\sNOPASSWD: ALL/%wheel ALL=\(ALL\) NOPASSWD: ALL/' /etc/sudoers

USER node
ENV NPM_CONFIG_PREFIX=/home/node/.npm-global
ENV PATH=$PATH:/home/node/.npm-global/bin

RUN npm install -g truffle openzeppelin-solidity

ENTRYPOINT ["/bin/sh"]
