FROM python:3.7-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories \
	&& apk add curl gcc libc-dev zlib-dev jpeg-dev chromium chromium-chromedriver font-adobe-100dpi ttf-dejavu fontconfig \
	&& pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple \
	&& pip3 install request waitress Selenium bs4 oss2 flask openpyxl numpy pillow