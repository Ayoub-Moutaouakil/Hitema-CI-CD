FROM node:18-alpine as build

WORKDIR /react-vite-app

COPY package.json package-lock.json ./

RUN npm install --silent

COPY . ./

RUN npm run build

##############################################################

FROM nginx:latest

COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

WORKDIR /usr/share/nginx/html

COPY --from=build /react-vite-app/dist/ .