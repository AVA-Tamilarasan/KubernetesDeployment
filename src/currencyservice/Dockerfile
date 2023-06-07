FROM node:20.2.0-alpine@sha256:31ec13908b942ca8b2b05e523c4e4a0f303a89bd75e57a81a241b5fd35677f60 as base

FROM base as builder

RUN apk add --update --no-cache \
    python3 \
    make \
    g++

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install --only=production

FROM base as without-grpc-health-probe-bin

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/node_modules ./node_modules

COPY . .

EXPOSE 7000

ENTRYPOINT [ "node", "server.js" ]
