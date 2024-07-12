# Etapa de construção
FROM node:14-alpine as build

# Defina o diretório de trabalho no contêiner
WORKDIR /app

# Copie o package.json e o package-lock.json
COPY package*.json ./

# Instale as dependências
RUN npm install

# Copie todo o código da aplicação para o diretório de trabalho
COPY . .

# Construa a aplicação para produção
RUN npm run build

# Etapa de produção
FROM nginx:alpine

# Copie os arquivos de build do estágio anterior para o diretório NGINX
COPY --from=build /app/build /usr/share/nginx/html

# Exponha a porta em que o NGINX está ouvindo
EXPOSE 3000

# Comando para rodar o NGINX
CMD ["nginx", "-g", "daemon off;"]
