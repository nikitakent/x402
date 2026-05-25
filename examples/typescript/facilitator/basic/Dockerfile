FROM node:22-alpine

RUN npm install -g pnpm

WORKDIR /app

# Copy everything from repo root
COPY . .

# Install and build the typescript packages first
WORKDIR /app/typescript
RUN pnpm install --frozen-lockfile
RUN pnpm build

# Now run the facilitator
WORKDIR /app/examples/typescript/facilitator/basic
RUN pnpm install

EXPOSE 4022

CMD ["node", "index.ts"]