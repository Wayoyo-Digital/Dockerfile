FROM ubuntu:24.04

LABEL maintainer=dfproffesional@gmail.com \
      vendor="Wayoyo Digital"

ENV TERM="xterm" \
    LANG="C.UTF-8" \
    LC_ALL="C.UTF-8"

# Layout copy (from staged image)
COPY --from=wayoyo/utilitybox:0.2 /layout/sbin/* /sbin/
COPY --from=wayoyo/utilitybox:0.2 /layout/usr/local/bin/* /usr/local/bin/


RUN set -x \
    # Init bootstrap
    && /usr/local/bin/apt-update \
    # System update
    && /usr/local/bin/apt-upgrade \
    # Install base stuff
    && apt-install \
        ca-certificates \
        apt-transport-https \
        zip \
        unzip \
        bzip2 \
        p7zip \
        sudo \
        curl \
        wget \
        patch \
        moreutils \
        dnsutils \
        openssh-client \
        rsync \
    && apt-add-repository multiverse \
    && apt-update \
    # && chmod +s /sbin/gosu \
    && wget -O /usr/share/oh-my-posh.theme.json https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/refs/heads/main/themes/robbyrussell.omp.json \
    && /usr/local/bin/generate-dockerimage-info \
    && /usr/local/bin/docker-image-cleanup