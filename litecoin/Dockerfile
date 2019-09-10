FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/litecoin/bin
ENV LITECOIN_VERSION 0.17.1

ADD https://download.litecoin.org/litecoin-${LITECOIN_VERSION}/linux/litecoin-${LITECOIN_VERSION}-x86_64-linux-gnu.tar.gz /tmp
RUN cd /opt \
 && tar zxvf /tmp/litecoin-${LITECOIN_VERSION}-x86_64-linux-gnu.tar.gz \
 && mv litecoin-${LITECOIN_VERSION} litecoin \
 && rm /tmp/litecoin-${LITECOIN_VERSION}-x86_64-linux-gnu.tar.gz

WORKDIR /opt/litecoin/bin
CMD ["/opt/litecoin/bin/litecoind"]
EXPOSE 9332
