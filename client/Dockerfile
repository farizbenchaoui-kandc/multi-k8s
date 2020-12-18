#build phase
FROM node:alpine as builder 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

#run phase
FROM nginx
EXPOSE 3000
#copy default conf file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#copy built files to nginx directory
COPY --from=builder /app/build /usr/share/nginx/html