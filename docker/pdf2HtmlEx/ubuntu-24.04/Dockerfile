FROM pdf2htmlex/pdf2htmlex:0.18.8.rc2-master-20200820-ubuntu-20.04-x86_64 AS pdf2htmlex-libs

RUN mkdir -p /download/x86_64-linux-gnu/ \
    && cp /usr/lib/x86_64-linux-gnu/libcairo.so.2 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libjpeg.so.8 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libpng16.so.16 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libfreetype.so.6 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libxcb.so.1 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libXrender.so.1 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libX11.so.6 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libXext.so.6 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libXau.so.6 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libpcre.so.3 /download/x86_64-linux-gnu \
    && cp /usr/lib/x86_64-linux-gnu/libffi.so.7 /download/x86_64-linux-gnu

FROM wayoyo/python:latest

LABEL maintainer="Wayoyo Digital <dfproffesional@gmail.com>"
LABEL org.opencontainers.image.title="pdf2htmlEX Python Dev"
LABEL org.opencontainers.image.description="Ubuntu 24.04 image with pdf2htmlEX and Python dev tools"
LABEL org.opencontainers.image.source="https://github.com/Wayoyo-Digital/Dockerfile"

COPY --from=pdf2htmlex-libs /usr/local/bin/pdf2htmlEX /usr/local/bin/pdf2htmlEX
COPY --from=pdf2htmlex-libs /usr/local/share/pdf2htmlEX /usr/local/share/pdf2htmlEX
COPY --from=pdf2htmlex-libs /download/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu

