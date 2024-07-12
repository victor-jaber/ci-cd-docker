# Use a imagem base oficial do Node.js
FROM node:22-alpine

# Defina o diretório de trabalho no contêiner
WORKDIR /app

# Copie o arquivo package.json e package-lock.json
COPY package.json package-lock.json ./

# Instale as dependências
RUN npm install

# Limpe o cache do npm
RUN npm cache clean --force

# Copie todos os arquivos do projeto para o diretório de trabalho
COPY . .

# Construa o aplicativo para produção
RUN npm run build

# Exponha a porta na qual a aplicação irá rodar
EXPOSE 3000

# Comando para iniciar a aplicação
CMD ["npm", "run", "preview", "--", "--port", "3000", "--host"]

