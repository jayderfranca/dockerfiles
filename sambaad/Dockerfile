FROM alpine:latest

ENV TZ=Etc/GMT+3
ENV DOMAIN=DOMAIN
ENV REALM=DOMAIN.TLD

RUN apk update && \
    apk add --no-cache tzdata pwgen supervisor chrony samba-dc krb5 && \
    rm -rf /var/cache/apk/*

COPY --chmod=755 root/bin/init /bin
COPY --chmod=600 root/etc/supervisord.conf /etc
COPY --chmod=644 root/etc/chrony/chrony.conf /etc/chrony

ENTRYPOINT ["/bin/init"]






