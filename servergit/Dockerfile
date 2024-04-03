FROM alpine:latest

RUN apk update && \
    apk add --no-cache lighttpd git git-daemon git-gitweb perl-cgi && \
    rm -rf /var/cache/apk/*

RUN rm -rf /etc/lighttpd/* && \
    mkdir /srv/repositories

RUN git config --system http.receivepack true && \
    git config --system init.defaultBranch main

COPY root/etc/gitweb.conf /etc/
COPY root/etc/lighttpd/* /etc/lighttpd/
COPY root/bin/init /bin

RUN chmod +x /bin/init

VOLUME /srv/repositories

ENTRYPOINT ["/bin/init"]






