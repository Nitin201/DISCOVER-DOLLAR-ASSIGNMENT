# ---------- Build Angular app ----------
FROM node:18-alpine AS build

WORKDIR /app

COPY package.json ./
COPY package-lock.json* ./ 

RUN npm install

COPY . .

# Build Angular for production
RUN npm run build -- --configuration production

# ---------- Nginx to serve + reverse proxy ----------
FROM nginx:alpine

# Copy built Angular app
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html

# Remove default config and add our own
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
