FROM node:22-alpine

RUN apk add --no-cache python3 make g++

RUN npm install -g pnpm

WORKDIR /app

# Copy the full typescript directory (includes tsconfig.base.json)
COPY typescript ./typescript

COPY examples/typescript ./examples/typescript

WORKDIR /app/examples/typescript

ENV CI=true

RUN pnpm install --filter "@x402/core-facilitator-typescript..."

RUN pnpm --filter "@x402/core" build
RUN pnpm --filter "@x402/evm" build

WORKDIR /app/examples/typescript/facilitator/basic

EXPOSE 4022

CMD ["node_modules/.bin/tsx", "index.ts"]