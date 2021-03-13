FROM node:latest 
MAINTAINER Jeiel Miguel Lopes
ENV PORT=3000
COPY . /var/www
WORKDIR /var/www
#turn vpn on
RUN npm config set registry http://nexus3.betha.com.br/repository/npm-all/
RUN npm install
ENTRYPOINT npm start
EXPOSE $PORT