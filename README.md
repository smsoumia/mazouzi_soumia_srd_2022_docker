# mazouzi_soumia_srd_2022_docker

# Projet Docker Frontend
``` FROM node:alpine as builder
WORKDIR /frontend
COPY ./package.json /frontend
RUN npm install
COPY . .
CMD [ "npm", "run", "start" ] 
```



# Projet Docker Backend
```FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install # install tou

COPY . .

EXPOSE 8080

CMD ["npm","start"] 
```



# Projet Docker Docker-Compose

```version: "3.7"
services:
  mongodb:
    image: "mongo"
    ports:
      - "27017:27017" #Port pour notre base de donnée 
    volumes:
      - data:/data/db
  backend:
    build: ./backend
    ports:
      - "8080:8080" # Il s'agit du port par défaut de l’api disponible dans le code source du fichier server.js 
    depends_on: # dependance entre les services (mongodb)
      - mongodb
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"# Il s'agit du port de notre react.js pour notre frontend
    stdin_open: true
    tty: true
    depends_on: #dependance entre les services (backend) 
      - backend
volumes: 
  data:
```
