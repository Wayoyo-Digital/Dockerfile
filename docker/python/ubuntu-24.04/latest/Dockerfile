FROM wayoyo/base:0.1

LABEL org.opencontainers.image.title="wayoyo/python:latest"
LABEL org.opencontainers.image.description="Python dev container on Ubuntu 24.04 with oh-my-posh and macchina"
LABEL org.opencontainers.image.version="latest"
LABEL org.opencontainers.image.authors="Daniel <dfproffesional@gmail.com>"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.source="https://github.com/Wayoyo-Digital/Dockerfile/blob/GITHUB-10/docker/python/ubuntu-24.04/latest/Dockerfile"
LABEL org.opencontainers.image.documentation="https://raw.githubusercontent.com/Wayoyo-Digital/Dockerfile/refs/heads/GITHUB-10/docker/python/ubuntu-24.04/latest/README.MD"
LABEL org.opencontainers.image.vendor="Wayoyo"
LABEL org.opencontainers.image.url="https://github.com/Wayoyo-Digital/Dockerfile"
LABEL org.opencontainers.image.base.name="wayoyo/base:0.1"

COPY --from=python:bookworm /usr/local /usr/local

WORKDIR /app
EXPOSE 8000

CMD [ "bash" ]