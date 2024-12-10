# Ruben Abreu Gonzalez
## Tutorial Prestashop

### Crear el docker compose
```yml
version: '3'
services:
  mysql:
    container_name: some-mysql
    image: mysql:5.7
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: admin
      MYSQL_DATABASE: prestashop
    networks:
      - prestashop_network
  prestashop:
    container_name: prestashop
    image: prestashop/prestashop:latest # Latest stable version of the PrestaShop, to see all available images go to ...
    restart: unless-stopped
    depends_on:
      - mysql
    ports:
      - 8080:80
    environment:
      DB_SERVER: some-mysql
      DB_NAME: prestashop
      DB_USER: root
      DB_PASSWD: admin
    networks:
      - prestashop_network
networks:
    prestashop_network:
```

### Levantar el contenedor y realizar la configuracion
> docker-compose up

### Conectarnos a la base de datos
> docker exec -it prestashop bash
```bash
Borramos la carpeta install
> rm -rf install

Cambiamos el nombre de la carpeta admin
> mv admin admin1
```

### Conectarse a la página
> http://localhost:8080/admin1