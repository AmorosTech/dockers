FROM python:3.7-alpine

RUN apk add curl gcc libc-dev zlib-dev jpeg-dev chromium chromium-chromedriver \
  && pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple \
  && pip3 install request waitress Selenium bs4 oss2 flask openpyxl numpy pillow \
  && rm -fr \
    /tmp/* \
    /root/.cache \
    /var/cache/apk/*
