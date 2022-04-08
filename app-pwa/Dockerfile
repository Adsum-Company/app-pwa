FROM node:14.18.0 AS compile-front-app-pwa

WORKDIR /opt/ng
COPY package*.json ./
RUN npm install

COPY . ./
RUN npm run build-prod

FROM nginx AS nginx-app-pwa

COPY --from=compile-front-app-pwa /opt/ng/dist/app-pwa /usr/share/nginx/html
COPY nginx/default.conf /etc/nginx/conf.d

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
