FROM yobasystems/alpine-mariadb AS builder

# build off of yobasystems/alpine-mariadb but we might as well optimize it
RUN apk add --no-cache binutils && \
find /bin /lib /sbin /usr/bin /usr/lib /usr/sbin -type f -exec strip -v {} \; && \
rm -f /var/cache/apk/* && \
cp /usr/bin/mysql_upgrade /usr/bin/mysql_upgrade.bak && \ 
apk del mariadb-server-utils binutils && \
cp /usr/bin/mysql_upgrade.bak /usr/bin/mysql_upgrade

# base off of scratch to squash build layers as small as possible
FROM scratch
LABEL maintainer="IF Fulcrum <fulcrum@ifsight.net>"
COPY --from=builder / /
# alter run script to allow for blank root passwords for local dev
COPY run.sh /scripts/run.sh

EXPOSE 3306

VOLUME ["/var/lib/mysql"]

ENTRYPOINT ["/scripts/run.sh"]
