FROM golang:1.20.4-alpine@sha256:0a03b591c358a0bb02e39b93c30e955358dadd18dc507087a3b7f3912c17fe13 AS builder
RUN apk add --no-cache ca-certificates git
RUN apk add build-base

WORKDIR /src
# restore dependencies
COPY go.mod go.sum ./
RUN go mod download
COPY . .

# Skaffold passes in debug-oriented compiler flags
ARG SKAFFOLD_GO_GCFLAGS
RUN go build -gcflags="${SKAFFOLD_GO_GCFLAGS}" -o /productcatalogservice .


RUN apk add --no-cache ca-certificates

WORKDIR /src

COPY . .

COPY products.json .

ENV GOTRACEBACK=single

EXPOSE 3550

ENTRYPOINT ["/src/server"]
