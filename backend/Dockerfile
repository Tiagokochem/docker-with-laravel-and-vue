# Use uma imagem base do PHP
FROM php:8.1-fpm

# Instale as dependências necessárias incluindo o Composer
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    curl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && rm -rf /var/lib/apt/lists/*

# Copie o código-fonte do backend para o container
COPY . /var/www/html

# Defina o diretório de trabalho
WORKDIR /var/www/html

# Verifique se o composer está disponível
RUN composer --version

# Cria um composer.json básico se não existir
RUN if [ ! -f composer.json ]; then echo "{ \"require\": {} }" > composer.json; fi

# Agora o Composer está disponível para uso
RUN composer install --no-dev --optimize-autoloader

# Exponha a porta do servidor web (por exemplo, 9000)
EXPOSE 9000

# Comando para iniciar o servidor
CMD ["php-fpm"]
