FROM node:20-alpine AS builder
ENV NODE_ENV = production

WORKDIR /app

COPY client/package.json .
RUN yarn install --frozen-lockfile --production=false

COPY client .

RUN npm run build


FROM nginx:1.27-alpine AS production
ENV NODE_ENV = production

COPY --from=builder /app/build /usr/share/nginx/html

COPY ./client/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
