FROM openjdk:8-alpine

ENV TZ='Asia/Shanghai'

RUN apk --no-cache add curl \
  && apk add --no-cache msttcorefonts-installer ttf-dejavu fontconfig \
  && update-ms-fonts \
  && fc-cache -f \
  && rm -rf /var/cache/*
