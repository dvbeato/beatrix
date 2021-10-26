FROM amazoncorretto:17-alpine

ENV ZK_VERSION apache-zookeeper-3.7.0-bin
ENV ZOO_4LW_COMMANDS_WHITELIST "*"

COPY ./${ZK_VERSION}.tar.gz /tmp/${ZK_VERSION}.tar.gz

RUN apk add --no-cache bash docker coreutils su-exec

RUN tar -xf /tmp/${ZK_VERSION}.tar.gz -C /opt \
  && rm -rf /tmp/* \
  && mv /opt/${ZK_VERSION} /opt/zookeeper

WORKDIR /opt/zookeeper

COPY zoo.cfg /opt/zookeeper/conf/zoo.cfg

EXPOSE 2181

CMD ["bin/zkServer.sh", "--config", "conf", "start-foreground"]

