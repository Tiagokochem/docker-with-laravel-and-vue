# Use uma imagem base do Node.js
FROM node:14

# Defina o diretório de trabalho
WORKDIR /app

# Copie o código-fonte do frontend para o container
COPY . .

# Verifique se o arquivo package.json está presente
RUN if [ ! -f package.json ]; then npm init -y; fi

# Instale as dependências do projeto
RUN npm install

# Adiciona o script "start" ao package.json se ele não existir
RUN if! grep -q "start" package.json; then \
        echo '{ "scripts": { "start": "node server.js" } }' >> package.json; \
    fi

# Exponha a porta do servidor web (por exemplo, 3000)
EXPOSE 3000

# Comando para iniciar o servidor
CMD ["npm", "start"]
