FROM amazoncorretto:17-alpine

ENV KAFKA_VERSION kafka_2.12-3.0.0

COPY ./${KAFKA_VERSION}.tgz /tmp/${KAFKA_VERSION}.tgz

RUN apk add --no-cache bash docker coreutils su-exec

RUN tar -xf /tmp/${KAFKA_VERSION}.tgz -C /opt \
  && rm -rf /tmp/* \
  && mv /opt/${KAFKA_VERSION} /opt/kafka

WORKDIR /opt/kafka

COPY ./server.properties /opt/kafka/config/server.properties

EXPOSE 9092 2181

ENTRYPOINT ["bin/kafka-server-start.sh", "config/server.properties"]

