# The compose setup from the Technitium Console README, as one image: the console
# image's copier step happens here at build time instead of into a shared volume.
FROM ghcr.io/bygarcia/technitium-console:1.3.4 AS console

FROM technitium/dns-server:15.6.2

COPY --from=console /usr/share/technitium-console/ /tmp/console/
RUN cd /tmp/console \
    && sha256sum -c technitium-console.tar.gz.sha256 \
    && mkdir /opt/technitium-console \
    && tar --no-same-owner -xzf technitium-console.tar.gz -C /opt/technitium-console \
    && rm -rf /tmp/console

ENV DNS_SERVER_WEB_SERVICE_WWW_FOLDER_PATH=/opt/technitium-console

# /data is the app's persistent, backed-up folder (the compose file's /etc/dns).
CMD ["/data"]
