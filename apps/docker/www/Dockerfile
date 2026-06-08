FROM node:22-alpine

RUN npm install -g corepack@latest \
    && corepack enable \
    && corepack prepare pnpm@11.1.2 --activate

CMD ["mkdir", "/app/www/"]

WORKDIR /app/www/

COPY ./apps/www/ .

RUN pnpm install --frozen-lockfile
RUN pnpm add pm2-runtime sharp

RUN pnpm run build

EXPOSE 3000

CMD ["pnpm", "start"]
