FROM node:22-alpine

RUN npm install -g pnpm

WORKDIR /app

# Copy monorepo root files needed for workspace
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
COPY typescript/packages ./typescript/packages
COPY examples/typescript/facilitator/basic ./facilitator

WORKDIR /facilitator

RUN pnpm install --frozen-lockfile
RUN pnpm build

EXPOSE 4022

CMD ["node", "index.js"]