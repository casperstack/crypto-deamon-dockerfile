FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/bitcoin-abc/bin
ENV BITCOINABC_VERSION 0.20.1

ADD https://download.bitcoinabc.org/${BITCOINABC_VERSION}/linux/bitcoin-abc-${BITCOINABC_VERSION}-x86_64-linux-gnu.tar.gz /tmp
RUN cd /opt \
 && tar zxvf /tmp/bitcoin-abc-${BITCOINABC_VERSION}-x86_64-linux-gnu.tar.gz \
 && mv bitcoin-abc-${BITCOINABC_VERSION} bitcoin-abc \
 && rm /tmp/bitcoin-abc-${BITCOINABC_VERSION}-x86_64-linux-gnu.tar.gz

WORKDIR /opt/bitcoin-abc/bin
CMD ["/opt/bitcoin-abc/bin/bitcoind"]
EXPOSE 8332
