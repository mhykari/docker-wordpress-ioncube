## What's included in this image?
This image is based on the [official WordPress image](https://hub.docker.com/_/wordpress/). It includes the [ionCube Loader](https://www.ioncube.com/loaders.php) and increases the memory limit to use this image with the WordPress extension [Memberium](https://memberium.com/). In addition the maximum upload file size is increased to 128MB.

## Supported (tested) tags
Currently the following tags can be used. The image builds on the WordPress image with the same tag. You can also change the php version in the Dockerfile and build.yml file to create and use the image with different php versions.

* `php7.0-apache`
* `php7.1-apache`
* `php7.2-apache`
* `php7.4-apache`

## How to use this image
You can use the Dockerfile path to build the image in your own docker-compose.yml file, or you can run the build.yml file to create the image and then use that in your docker-compose.yml file
The image can be used identically to the official WordPress image. You can take a look at their description or use a **docker-compose.yml** similar like this:

```yml
version: '3.1'

services:
  wordpress:
    image: mhykari/wordpress-ioncube:php7.2-apache
    restart: always
    ports:
      - 80:80
    volumes:
      - ./wp-content/:/var/www/html/wp-content
    environment:
      - WORDPRESS_DB_HOST=mariadb
      - WORDPRESS_DB_PASSWORD: example

  mariadb:
    image: mariadb
    restart: always
    volumes: ./db-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: example

```
