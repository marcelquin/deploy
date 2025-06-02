# Etapa 1: build da aplicação React
FROM node:18-alpine AS build

WORKDIR /app

# Copia os arquivos do projeto
COPY . .

# Instala dependências e gera a build
RUN npm install && npm run build

# Etapa 2: Nginx para servir os arquivos da build
FROM nginx:alpine

# Remove a config padrão do Nginx
RUN rm /etc/nginx/conf.d/default.conf

# Copia a configuração customizada para servir SPAs (React)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copia a build gerada da etapa anterior para o Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Expor a porta 80
EXPOSE 80

# Comando para iniciar o Nginx
CMD ["nginx", "-g", "daemon off;"]
