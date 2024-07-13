FROM ubuntu:latest

# For above Ubuntu 24.04
RUN touch /var/mail/ubuntu && chown ubuntu /var/mail/ubuntu && userdel -r ubuntu ; exit 0

RUN set -x && \
    apt-get update && apt-get install -y --no-install-recommends openssl nfs-kernel-server && \
    rm -rf /var/lib/apt/lists/* \
    && mkdir -m 777 /exports

COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +rx /usr/local/bin/docker-entrypoint.sh

VOLUME /exports

EXPOSE 2049/tcp
EXPOSE 20048/tcp

ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]
CMD ["/exports"]
