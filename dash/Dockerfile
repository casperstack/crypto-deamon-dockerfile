FROM ubuntu:18.04
MAINTAINER labs@casperstack.com

RUN apt-get update && apt-get install -y \
    libzmq3-dev=4.2.* \
 && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/dashcore/bin
ENV DASH_VERSION 0.14.0
ENV DASH_RELEASE 3
ENV DASH_ZIP_SHA256SUM 28d45537e1c982967075742f9f6ff631d6de72d075091d53ff039ed8919714ba

ADD https://github.com/dashpay/dash/releases/download/v${DASH_VERSION}.${DASH_RELEASE}/dashcore-${DASH_VERSION}.${DASH_RELEASE}-x86_64-linux-gnu.tar.gz /tmp
RUN [ $DASH_ZIP_SHA256SUM = $(sha256sum /tmp/dashcore-${DASH_VERSION}.${DASH_RELEASE}-x86_64-linux-gnu.tar.gz | awk '{print $1}') ] \
 && cd /opt \
 && tar zxvf /tmp/dashcore-${DASH_VERSION}.${DASH_RELEASE}-x86_64-linux-gnu.tar.gz \
 && mv dashcore-${DASH_VERSION} dashcore \
 && rm /tmp/dashcore-${DASH_VERSION}.${DASH_RELEASE}-x86_64-linux-gnu.tar.gz

WORKDIR /opt/dashcore/bin
CMD ["/opt/dashcore/bin/dashd"]
EXPOSE 9998
