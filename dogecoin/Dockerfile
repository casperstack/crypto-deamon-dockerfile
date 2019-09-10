FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/dogecoin/bin
ENV DOGECOIN_VERSION 1.14.0

ADD https://github.com/dogecoin/dogecoin/releases/download/v${DOGECOIN_VERSION}/dogecoin-${DOGECOIN_VERSION}-x86_64-linux-gnu.tar.gz /tmp
RUN cd /opt \
 && tar zxvf /tmp/dogecoin-${DOGECOIN_VERSION}-x86_64-linux-gnu.tar.gz \
 && mv dogecoin-${DOGECOIN_VERSION} dogecoin \
 && rm /tmp/dogecoin-${DOGECOIN_VERSION}-x86_64-linux-gnu.tar.gz

WORKDIR /opt/dogecoin/bin
CMD ["/opt/dogecoin/bin/dogecoind"]
EXPOSE 22555 44555
