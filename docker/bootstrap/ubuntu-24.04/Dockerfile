FROM ubuntu:24.04

LABEL maintainer=dfproffesional@gmail.com \
      vendor=Wayoyo Digital

ENV TERM="xterm" \
    LANG="C.UTF-8" \
    LC_ALL="C.UTF-8"

# Layout copy (from staged image)
COPY --from=wayoyo/utilitybox /layout/sbin/* /sbin/
COPY --from=wayoyo/utilitybox /layout/usr/local/bin/* /usr/local/bin/


RUN set -x \
    # Init bootstrap
    && apt-update \
    # System update
    && /usr/local/bin/apt-upgrade \
    # Install base stuff
    && apt-install \
        ca-certificates \
        apt-transport-https \
    && apt-add-repository multiverse \
    && apt-update \
    && /usr/local/bin/generate-dockerimage-info \
    && docker-run-bootstrap \
    && docker-image-cleanup