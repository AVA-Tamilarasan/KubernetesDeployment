FROM node:20.2.0-alpine@sha256:31ec13908b942ca8b2b05e523c4e4a0f303a89bd75e57a81a241b5fd35677f60 as builder


RUN apk add --update --no-cache \
    python3 \
    make \
    g++

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install -g npm@latest

WORKDIR /usr/src/app

EXPOSE 7000

ENTRYPOINT [ "node", "server.js" ]

