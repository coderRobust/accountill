FROM node:20-alpine AS deps
WORKDIR /usr/src/app

COPY server/package.json .
RUN npm install

FROM node:20-alpine AS app
ENV NODE_ENV=production
WORKDIR /usr/src/app

COPY --from=deps /usr/src/app/node_modules ./node_modules
COPY server/ .


EXPOSE 5000
CMD ["yarn", "start"]
