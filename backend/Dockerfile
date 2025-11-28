FROM node:20-alpine

WORKDIR /usr/src/app

# copy package files first for caching
COPY package*.json ./
RUN npm install --omit=dev

# copy rest
COPY . .

ENV PORT=3000
EXPOSE 3000

CMD ["node", "server.js"]
