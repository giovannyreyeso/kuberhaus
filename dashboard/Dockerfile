FROM node:8.11.0 as builder

ADD . /root/kuberhaus
WORKDIR /root/kuberhaus

RUN npm install \ 
    && npm run build

FROM nginx:1.15.8-alpine
WORKDIR /var/www/kuberhaus
COPY --from=builder /root/kuberhaus/nginxconf/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /root/kuberhaus/dist /usr/share/nginx/html/
EXPOSE 80
