# Usa la imagen oficial de PrestaShop como base
FROM prestashop/prestashop:latest
# Instala nano
RUN apt-get update && apt-get install -y nano
# Elimina la caché de apt para reducir el tamaño de la imagen
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
# Define el directorio de trabajo dentro del contenedor
WORKDIR /var/www/html