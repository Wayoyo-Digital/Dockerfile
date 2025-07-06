FROM wayoyo/base:0.1

LABEL org.opencontainers.image.title="wayoyo/python"
LABEL org.opencontainers.image.description="Lightweight container for converting PDFs to HTML using MuPDF and Poppler"
LABEL org.opencontainers.image.version="latest"
LABEL org.opencontainers.image.authors="Daniel <dfproffesional@gmail.com>"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.source="https://github.com/Wayoyo-Digital/Dockerfile/blob/GITHUB-10/docker/python/ubuntu-24.04/latest/Dockerfile"
LABEL org.opencontainers.image.documentation="https://github.com/Wayoyo-Digital/Dockerfile#readme"
LABEL org.opencontainers.image.vendor="Wayoyo"

COPY --from=python:bookworm /usr/local /usr/local

WORKDIR /app
EXPOSE 8000

CMD [ "bash" ]