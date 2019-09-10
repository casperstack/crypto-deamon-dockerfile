FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/monero/bin
ENV MONERO_VERSION 0.14.1.2
ENV MONERO_ZIP_SHA256SUM a4d1ddb9a6f36fcb985a3c07101756f544a5c9f797edd0885dab4a9de27a6228

ADD https://downloads.getmonero.org/cli/monero-linux-x64-v${MONERO_VERSION}.tar.bz2 /tmp/
RUN [ $MONERO_ZIP_SHA256SUM = $(sha256sum /tmp/monero-linux-x64-v${MONERO_VERSION}.tar.bz2 | awk '{print $1}') ] \
  && mkdir -p /opt/monero/data && cd /opt/monero \
  && tar zxvf /tmp/monero-linux-x64-v${MONERO_VERSION}.tar.bz2 \
  && mv monero-x86_64-linux-gnu bin \
  && rm /tmp/monero*.bz2
 
WORKDIR /opt/monero/bin
CMD ["/opt/monero/bin/monerod"]

# p2p-bind-port : mainnet, testnet, stagenet
EXPOSE 18080 28080 38080

# rpc-bind-port : mainnet, testnet, stagenet
EXPOSE 18081 28081 38081

# zmq-rpc-bind-port : mainnet, testnet, stagenet
EXPOSE 18082 28082 38082

