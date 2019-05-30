FROM node:8-alpine

RUN npm install -g ganache-cli
RUN mkdir -p /var/ganache

ENV DOCKER true
ENV DATADIR /var/ganache
ENV MNEMONIC twelve social common shadow ski provide surge stem welcome eight tomorrow method
ENV NETWORKID 1234

EXPOSE 8545

ENTRYPOINT ["sh", "-c", "ganache-cli -v --host=0.0.0.0 --db=${DATADIR} --mnemonic=\"${MNEMONIC}\" --networkId=${NETWORKID}"]
