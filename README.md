Stworzyłem projekt docker-compose.yml
działa wszystko elegancko

<img src='png.png'>

docker-compose.yml

```
version: '3'
services:
    php-apache:
        image: php:7.2.1-apache
        ports:
            - 80:80
        volumes:
            - ./DocumentRoot:/var/www/html
        links:
            - 'mysqldb'
    mysqldb:
        image: mysql
        privileged: true
        tty: true
        ports:
          - 6666:3306
        volumes:
          - mysql:/var/lib/mysql
        environment:
          TZ: "Europe/Rome"
          MYSQL_ALLOW_EMPTY_PASSWORD: "no"
          MYSQL_ROOT_PASSWORD: "dupadupa"
          MYSQL_USER: 'wmaj'
          MYSQL_PASSWORD: 'dupadupa'
          MYSQL_DATABASE: 'db'

volumes:
  mysql:

  ```