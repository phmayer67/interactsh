# Build
FROM golang:1.17-alpine AS build-env
RUN apk add build-base
RUN go install -v git@github.com:phmayer67/interactsh/cmd/interactsh-server@latest

# Release
FROM alpine:3.14
RUN apk -U upgrade --no-cache \
    && apk add --no-cache bind-tools ca-certificates
COPY --from=build-env /go/bin/interactsh-server /usr/local/bin/interactsh-server

ENTRYPOINT ["interactsh-server"]