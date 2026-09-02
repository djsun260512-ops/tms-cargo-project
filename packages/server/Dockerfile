FROM node:20-alpine

WORKDIR /app

RUN corepack enable && corepack prepare pnpm@9.15.5 --activate

COPY package.json pnpm-lock.yaml pnpm-workspace.yaml tsconfig.base.json ./
COPY packages ./packages

RUN pnpm install --frozen-lockfile

EXPOSE 3000

CMD ["sh", "-lc", "pnpm build:shared && pnpm --filter @open-trade/server db:migrate && pnpm --filter @open-trade/server db:seed && pnpm dev:server"]
