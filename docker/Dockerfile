# Aurora Home Server — built from the latest release (see compose.yaml).
FROM node:24-alpine
ADD https://github.com/Loganpnorton/aurora-tv/releases/latest/download/aurora-server-bundle.tgz /tmp/aurora.tgz
RUN mkdir -p /app /data && tar -xzf /tmp/aurora.tgz -C /app && rm /tmp/aurora.tgz
ENV AURORA_DATA_DIR=/data \
    AURORA_WEB_ROOT=/app \
    AURORA_NO_BROWSER=1 \
    NODE_ENV=production
VOLUME /data
EXPOSE 8484/tcp 8485/udp
CMD ["node", "/app/aurora-server.cjs"]
