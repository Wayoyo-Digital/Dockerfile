# Build & Compile
FROM alpine:latest AS builder

RUN apk add --no-cache \
    bash \
    curl \
    bash \
    wget \
    build-base \
    musl-dev \
    openssl-dev \
    pkgconfig \
    libffi-dev \
    && mkdir -p \
        /download/sbin \
        /download/usr/local/bin \
    # layout scripts
    && wget -O /tmp/layout-install.sh https://raw.githubusercontent.com/Wayoyo-Digital/Docker-BaseLayout/refs/heads/main/install.sh \
    && sh /tmp/layout-install.sh /download \
    && "/download/usr/local/bin/cli-macchina" \
    && curl -s https://ohmyposh.dev/install.sh | bash -s -- -d /download/usr/local/bin

FROM alpine:latest

COPY --from=builder /download /layout
COPY --from=builder /usr/local/bin/macchina /layout/usr/local/bin/macchina

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
    # Install gosu
    && wget -O "/layout/sbin/gosu" "https://github.com/tianon/gosu/releases/download/1.17/gosu-amd64" \
    && wget -O "/tmp/gosu.asc" "https://github.com/tianon/gosu/releases/download/1.17/gosu-amd64.asc" \
    && export GNUPGHOME="$(mktemp -d)" \
    && gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
    && gpg --batch --verify /tmp/gosu.asc "/layout/sbin/gosu" \
    && rm -rf "$GNUPGHOME" /tmp/gosu.asc \
    && chmod +x "/layout/sbin/gosu" \
    && "/layout/sbin/gosu" nobody true
