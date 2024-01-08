FROM node:16.19.1-alpine3.16 as base

FROM base as local
WORKDIR /usr/src/app
COPY ["package.json","package-lock.json","./"]
RUN apk --no-cache --virtual build-dependencies \
    add python3 make g++ \
    && npm ci \
    && apk del build-dependencies
COPY . .
EXPOSE 5173
CMD ["npm","run","dev"]