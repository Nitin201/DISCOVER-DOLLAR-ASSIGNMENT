FROM node:18-alpine

# Create app directory
WORKDIR /app

# Install dependencies
COPY package.json ./
# If you add package-lock.json later, this still works
COPY package-lock.json* ./

RUN npm install --only=production

# Copy rest of the code
COPY . .

# Environment
ENV PORT=8080
ENV MONGODB_URL=mongodb://mongo:27017/dd_db

EXPOSE 8080

CMD ["node", "server.js"]
