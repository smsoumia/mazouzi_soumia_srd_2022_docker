# mazouzi_soumia_srd_2022_docker
# Projet Docker
``` FROM node:alpine as builder
WORKDIR /frontend
COPY ./package.json /frontend
RUN npm install
COPY . .
CMD [ "npm", "run", "start" ] 
```
