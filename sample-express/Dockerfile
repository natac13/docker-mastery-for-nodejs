FROM node:12.2.0-alpine

EXPOSE 3000

ENV NODE_ENV=production

RUN mkdir -p /node/app/node_modules && chown -R node:node /node

WORKDIR /node

COPY package.json package-lock*.json ./

RUN npm ci && npm cache clean --force

USER node

WORKDIR /node/app

COPY --chown=node:node ./ ./

CMD ["node", "./bin/www"]
