# Etapa 1: build (caso você esteja usando Vue, React, Angular, etc.)
# Comente esta etapa se você já tem a pasta `dist` ou `build` pronta.

# FROM node:18-alpine AS build-stage
# WORKDIR /app
# COPY . .
# RUN npm install && npm run build

# Etapa 2: Nginx para servir os arquivos

FROM nginx:alpine
# Remove a configuração padrão
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copia sua configuração customizada do Nginx (opcional, veja abaixo)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copia os arquivos da build do frontend
# Se estiver usando a build acima:
# COPY --from=build-stage /app/dist /usr/share/nginx/html

# Se você já tem a pasta `dist/` ou `build/` pronta:
COPY dist/ /usr/share/nginx/html

# Expõe a porta padrão do Nginx
EXPOSE 80

# Comando padrão
CMD ["nginx", "-g", "daemon off;"]
