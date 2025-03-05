FROM node:22 as build

WORKDIR /app

# Copie package.json et installe les dépendances
COPY frontend/package*.json ./
RUN npm install -g npm@latest
RUN npm install

# Copie tout le projet
COPY frontend/. .  

# Build l’application Angular
RUN npm run build

FROM nginx:latest

# Copie le build Angular dans Nginx
COPY --from=build /app/dist/frontend /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

