# docker-mozjpeg

[![](https://img.shields.io/docker/stars/dmcpartners/docker-mozjpeg.svg)](https://hub.docker.com/r/dmcpartners/docker-mozjpeg 'DockerHub') 
[![](https://img.shields.io/docker/pulls/dmcpartners/docker-mozjpeg.svg)](https://hub.docker.com/r/dmcpartners/docker-mozjpeg 'DockerHub') 
[![](https://images.microbadger.com/badges/image/dmcpartners/docker-mozjpeg.svg)](https://microbadger.com/images/dmcpartners/docker-mozjpeg "Get your own image badge on microbadger.com")

## Usage

Use multi-stage builds based on this image saved my life. 

Example:

```Dockerfile
FROM dmcpartners/docker-mozjpeg as builder

FROM node:10-alpine
WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install --only=production

COPY --from=builder /usr/local /usr/local

COPY . .

CMD [ "npm", "start" ]
```

Note: all binary files of mozjpeg will be located in `/usr/local/bin`, e.g. `/usr/local/bin/jpegtran`.
