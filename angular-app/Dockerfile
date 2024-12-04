# Step 1: Build teh app in image 'build'
FROM node:16-alpine AS build

WORKDIR /app
COPY package*.json ./
RUN npm install --force
COPY . .
RUN npm run build --force

# Step 2: run
FROM nginx:1.17.1-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/angular-app /usr/share/nginx/html

