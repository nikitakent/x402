FROM node:22-alpine

RUN npm install -g pnpm

WORKDIR /app

COPY . .

WORKDIR /app/typescript
RUN pnpm install
RUN pnpm build

WORKDIR /app/examples/typescript/facilitator/basic
RUN pnpm install

EXPOSE 4022

CMD ["node", "index.ts"]