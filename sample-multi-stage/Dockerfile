FROM node:10-slim as prod
ENV NODE_ENV=production

RUN mkdir -p /app && chown -R node:node /app

WORKDIR /app

COPY --chown=node:node package*.json ./

COPY --chown=node:node . .

USER node

RUN npm install --production && npm cache clean --force

FROM prod as dev
ENV NODE_ENV=development

RUN npm install --only=dev

FROM dev as test
ENV NODE_ENV=development