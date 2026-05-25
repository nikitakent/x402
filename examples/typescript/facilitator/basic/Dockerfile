FROM node:22-alpine

RUN npm install -g pnpm

WORKDIR /app

COPY . .

# Install and build everything from the monorepo root
RUN pnpm install
RUN pnpm --filter "@x402/core" build
RUN pnpm --filter "@x402/evm" build

WORKDIR /app/examples/typescript/facilitator/basic

EXPOSE 4022

CMD ["node_modules/.bin/tsx", "index.ts"]