FROM node:10-slim as prod
ENV NODE_ENV=production

RUN mkdir -p /app && chown -R node:node /app

WORKDIR /app

COPY --chown=node:node package*.json ./

COPY --chown=node:node . .

USER node

RUN npm install --only=production && npm cache clean --force

CMD [ "node", "./bin/www" ]

FROM prod as dev
ENV NODE_ENV=development

RUN npm install --only=development

CMD [ "./node_modules/nodemon/bin/nodemon.js", "./bin/www", "-inspect=0.0.0.0:9229" ]

FROM dev as test
ENV NODE_ENV=development

CMD [ "npm", "test" ]