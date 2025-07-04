FROM alpine:latest

RUN apk add --no-cache \
        ca-certificates \
        openssl \
        curl \
        bash \
        sed \
        wget \
        zip \
        unzip \
        bzip2 \
        p7zip \
        drill \
        ldns \
        openssh-client \
        rsync \
        git \
        gnupg \
    && mkdir -p \
        /layout/sbin \
        /layout/usr/local/bin \
    # layout scripts
    && wget -O /tmp/layout-install.sh https://raw.githubusercontent.com/Wayoyo-Digital/Docker-BaseLayout/refs/heads/main/install.sh \
    && sh /tmp/layout-install.sh /layout \
    # Install gosu
    && wget -O "/layout/sbin/gosu" "https://github.com/tianon/gosu/releases/download/1.17/gosu-amd64" \
    && wget -O "/tmp/gosu.asc" "https://github.com/tianon/gosu/releases/download/1.17/gosu-amd64.asc" \
    && export GNUPGHOME="$(mktemp -d)" \
    && gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
    && gpg --batch --verify /tmp/gosu.asc "/layout/sbin/gosu" \
    && rm -rf "$GNUPGHOME" /tmp/gosu.asc \
    && chmod +x "/layout/sbin/gosu" \
    && "/layout/sbin/gosu" nobody true
