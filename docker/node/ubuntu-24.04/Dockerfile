FROM wayoyo/base:0.1

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
