FROM node:20-bookworm-slim

WORKDIR /app

RUN apt-get update \
    && apt-get install -y --no-install-recommends bash ca-certificates coreutils gzip \
    && rm -rf /var/lib/apt/lists/*

COPY package.json ./package.json
RUN npm install --omit=dev \
    && npm cache clean --force

COPY index.js ./index.js
COPY start.sh ./start.sh
RUN chmod +x /app/start.sh

ENV NODE_ENV=production
ENV PORT=3000

EXPOSE 3000

CMD ["node", "index.js"]
