FROM docker.io/mariadb:10.0
MAINTAINER IF Fulcrum "fulcrum@ifsight.net"

RUN echo "Cache bust 201604291406"

# make it so that mysql has same UID and GID
ADD docker-entrypoint.sh /docker-entrypoint.sh
