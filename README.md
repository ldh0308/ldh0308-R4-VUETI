# Vue Dokerize
- Step #1
  ```bash
  $ vi Dockerfile
  # build stage
  FROM node:lts-alpine as build-stage
  WORKDIR /app
  COPY package*.json ./
  RUN npm install
  COPY . .
  RUN npm run build

  # production stage
  FROM nginx:stable-alpine as production-stage
  COPY --from=build-stage /app/docs /usr/share/nginx/html
  EXPOSE 80
  CMD ["nginx", "-g", "daemon off;"]
- step #2
  $ sudo docker build -t vue-app .
  $ sudo docker run -itd --name 240220.1 -p 8080:80 vue-app
  ```
