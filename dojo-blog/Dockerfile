FROM node:lts-alpine

RUN npm install -g http-server

WORKDIR /app
COPY package*.json .
RUN npm install -g @vue/cli-service
RUN npm install json-server
RUN npm install

COPY . .

RUN npm run build
EXPOSE 8080

CMD ["/bin/ash", "startup.sh"]

