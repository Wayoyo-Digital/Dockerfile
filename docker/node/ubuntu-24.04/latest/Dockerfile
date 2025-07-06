FROM wayoyo/base:0.1

LABEL org.opencontainers.image.title="wayoyo/node:latest"
LABEL org.opencontainers.image.description="Node.js dev container on Ubuntu 24.04 with pnpm"
LABEL org.opencontainers.image.version="latest"
LABEL org.opencontainers.image.authors="Daniel <dfproffesional@gmail.com>"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.source="https://raw.githubusercontent.com/Wayoyo-Digital/Dockerfile/refs/heads/main/docker/node/ubuntu-24.04/latest/Dockerfile"
LABEL org.opencontainers.image.documentation="https://raw.githubusercontent.com/Wayoyo-Digital/Dockerfile/refs/heads/main/docker/node/ubuntu-24.04/latest/README.MD"
LABEL org.opencontainers.image.vendor="Wayoyo"
LABEL org.opencontainers.image.url="https://github.com/Wayoyo-Digital/Dockerfile"
LABEL org.opencontainers.image.base.name="wayoyo/base:0.1"

COPY --from=node:bookworm /usr/local /usr/local

# Verificar que node y npm estén disponibles, luego instalar yarn y pnpm
RUN set -x \
    && node --version \
    && npm --version \
    && sudo npm install -g pnpm

# Exponer el puerto típico de desarrollo Node.js
WORKDIR /app
EXPOSE 3000

# Comando por defecto: bash interactivo
CMD [ "bash" ]
