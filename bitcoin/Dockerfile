FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/bitcoin/bin
ENV BITCOIN_VERSION 0.18.1

ADD https://bitcoin.org/bin/bitcoin-core-${BITCOIN_VERSION}/bitcoin-${BITCOIN_VERSION}-x86_64-linux-gnu.tar.gz /tmp
RUN cd /opt \
 && tar zxvf /tmp/bitcoin-${BITCOIN_VERSION}-x86_64-linux-gnu.tar.gz \
 && mv bitcoin-${BITCOIN_VERSION} bitcoin \
 && rm /tmp/bitcoin-${BITCOIN_VERSION}-x86_64-linux-gnu.tar.gz

WORKDIR /opt/bitcoin/bin
CMD ["/opt/bitcoin/bin/bitcoind"]
EXPOSE 8332
