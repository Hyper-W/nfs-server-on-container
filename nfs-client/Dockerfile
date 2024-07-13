FROM ubuntu:latest

# For above Ubuntu 24.04
RUN touch /var/mail/ubuntu && chown ubuntu /var/mail/ubuntu && userdel -r ubuntu ; exit 0

# Your Property
ARG USER=user
ARG USER_ID=1000
ARG GROUP_ID=1000

RUN apt-get update && apt-get install -y --no-install-recommends sudo openssl nfs-common nano && \
    rm -rf /var/lib/apt/lists/* \
    && groupadd -g "${GROUP_ID}" "${USER}" \
    && useradd -u "${USER_ID}" -m -s /bin/bash -g "${USER}" -G sudo "${USER}" \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN mkdir -pm 777 /mnt/test

USER ${USER}