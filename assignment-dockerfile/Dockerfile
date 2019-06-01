# fill in the blanks to dockerize this node app
FROM node:10.15-alpine

EXPOSE 3000

RUN apk add --no-cache tini

RUN mkdir /app && chown -R node:node /app

WORKDIR /app

COPY --chown=node:node package*.json ./

USER node

RUN npm install && npm cache clean --force

COPY --chown=node:node . .

# ENTRYPOINT ["/sbin/tini", "--"]

CMD ["node", "./app.js"]
