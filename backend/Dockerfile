FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --only=production

COPY . .

ENV PORT=8080
ENV MONGODB_URL=mongodb://mongo:27017/dd_db

EXPOSE 8080

CMD ["node", "server.js"]
