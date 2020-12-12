FROM node:12.18.1

RUN mkdir app

WORKDIR /app

ADD . /app

RUN yarn install

EXPOSE 3333

CMD ["yarn", "serve"]
