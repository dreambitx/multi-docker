FROM node:alpine as builder

WORKDIR '/app'
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# elastic beanstalk will auto map this port
EXPOSE 3000 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html