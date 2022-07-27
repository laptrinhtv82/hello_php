FROM vinhio/php8:latest

VOLUME /home/www/app
EXPOSE 80 443

# Replace default nginx user and group with IDs, matching current host user (developer)
ARG hostUID=1000
ARG hostGID=1000
ENV hostUID=$hostUID
ENV hostGID=$hostGID
RUN echo "uid:gid=$hostUID:$hostGID" &&\
    oldUID=`id -u nginx` &&\
    deluser nginx &&\
    addgroup -g $hostGID nginx &&\
    adduser -S -u $hostUID -G nginx -h /home/www -s /sbin/nologin nginx &&\
    find /var -user $oldUID -exec chown -v $hostUID:$hostGID {} \;
