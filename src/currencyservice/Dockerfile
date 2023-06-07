
FROM node:20.2.0-alpine@sha256:f25b0e9d3d116e267d4ff69a3a99c0f4cf6ae94eadd87f1bf7bd68ea3ff0bef7 as base

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE  7000

CMD [ "npm", "start" ]
