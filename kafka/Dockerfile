FROM registry.cn-shanghai.aliyuncs.com/amoros/openjdk:8-alpine

ENV TZ='Asia/Shanghai'

ENV KAFKA_VERSION 1.1.0
ENV SCALA_VERSION 2.12

LABEL name="kafka-connect" version=${KAFKA_VERSION}

RUN apk add --no-cache bash coreutils su-exec
RUN apk add --no-cache -t .build-deps curl ca-certificates jq \
  && mkdir -p /opt \
  && mirror=$(curl --stderr /dev/null https://www.apache.org/dyn/closer.cgi\?as_json\=1 | jq -r '.preferred') \
  && curl -sSL "${mirror}kafka/${KAFKA_VERSION}/kafka_${SCALA_VERSION}-${KAFKA_VERSION}.tgz" \
  | tar -xzf - -C /opt \
  && mv /opt/kafka_${SCALA_VERSION}-${KAFKA_VERSION} /opt/kafka \
  && adduser -DH -s /sbin/nologin kafka \
  && chown -R kafka: /opt/kafka \
  && rm -rf /tmp/* \
  && apk del --purge .build-deps

ENV PATH /sbin:/opt/kafka/bin/:$PATH

WORKDIR /home/kafka

EXPOSE 8083

ENTRYPOINT ["/opt/kafka/bin/connect-distributed.sh", "config/connect-distributed.properties"]