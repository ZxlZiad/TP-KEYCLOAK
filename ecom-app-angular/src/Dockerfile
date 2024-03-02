FROM node:14 AS build

WORKDIR /app

COPY ecom-app-angular/package*.json /app/

RUN npm install

COPY ecom-app-angular/ /app/

RUN npm run build -- --prod

FROM nginx:alpine

COPY --from=build /app/dist/ecom-app-angular /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
