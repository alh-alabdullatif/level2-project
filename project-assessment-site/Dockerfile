FROM node:lts-alpine3.10


WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./

RUN npm install


COPY . .

EXPOSE 80
CMD [ "node", "index.js" ]
