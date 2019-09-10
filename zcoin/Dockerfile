FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/zcoin/bin
ENV ZCOIN_VERSION 0.13.8
ENV ZCOIN_RELEASE 4
ENV ZCOIN_ZIP_SHA256SUM 201a6b9d9734d20791a79d64f5bb3188f7c9a7ac89adb89143a004cda38bbd00

ADD https://github.com/zcoinofficial/zcoin/releases/download/v${ZCOIN_VERSION}.${ZCOIN_RELEASE}/zcoin-${ZCOIN_VERSION}.${ZCOIN_RELEASE}-linux64.tar.gz /tmp

RUN [ $ZCOIN_ZIP_SHA256SUM = $(sha256sum /tmp/zcoin-${ZCOIN_VERSION}.${ZCOIN_RELEASE}-linux64.tar.gz | awk '{print $1}') ] \
 && cd /opt \
 && tar zxvf /tmp/zcoin-${ZCOIN_VERSION}.${ZCOIN_RELEASE}-linux64.tar.gz \
 && mv zcoin-${ZCOIN_VERSION} zcoin \
 && rm /tmp/zcoin-${ZCOIN_VERSION}.${ZCOIN_RELEASE}-linux64.tar.gz

WORKDIR /opt/zcoin/bin
CMD ["/opt/zcoin/bin/zcoind"]
EXPOSE 8888
