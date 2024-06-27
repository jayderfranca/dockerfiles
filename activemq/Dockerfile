FROM openjdk:8-jre-alpine

LABEL maintainer="Jayder França <jayderfranca@gmail.com>"

ARG ACTIVEMQ_URL=nourl
ARG ACTIVEMQ_VERSION=noversion

ENV ACTIVEMQ_URL=$ACTIVEMQ_URL
ENV ACTIVEMQ_VERSION=$ACTIVEMQ_VERSION

ADD activemq.tar.gz /tmp/
COPY root/bin/init /bin/init

RUN mv /tmp/*-activemq-* /opt/activemq \
 && chmod +x /bin/init \
 && mkdir -p /var/opt/activemq/data \
 && mkdir -p /var/log/activemq \
 && mkdir -p /tmp/activemq \
 && rm -fR /opt/activemq/activemq-all-*.jar >/dev/null \
 && rm -fR /opt/activemq/examples >/dev/null \
 && rm -fR /opt/activemq/webapps-demo >/dev/null \
 && rm -fR /opt/activemq/data >/dev/null \
 && rm -fR /opt/activemq/bin/linux-* >/dev/null \
 && rm -fR /opt/activemq/bin/macosx >/dev/null \
 && rm -fR /opt/activemq/bin/wrapper.jar >/dev/null \
 && mv /opt/activemq/conf /var/opt/activemq >/dev/null \
 && mkdir /opt/activemq/config >/dev/null \
 && mv /var/opt/activemq/conf/log4j.properties /opt/activemq/config/log4j.properties >/dev/null \
 && mv /var/opt/activemq/conf/login.config /opt/activemq/config/login.config >/dev/null \
 && mv /var/opt/activemq/conf/logging.properties /opt/activemq/config/logging.properties >/dev/null

ENTRYPOINT ["/bin/init"]
