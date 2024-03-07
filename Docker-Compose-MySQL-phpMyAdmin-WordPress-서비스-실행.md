# `Docker Compose` -  `MySQL, phpMyAdmin, WordPress 실행` 설정

## docker-compose.yml 코드
이 코드는 Docker Compose를 사용하여 MySQL 데이터베이스, phpMyAdmin, 그리고 WordPress를 실행하는 설정입니다. 각 서비스는 별도의 컨테이너에서 실행되며, 모두 같은 네트워크(wpsite)를 공유합니다.



```yml
version: '3'

services:
  # Database
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootroot
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpresswordpress
    networks:
      - wpsite
  # phpmyadmin
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - '8080:80'
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: rootroot 
    networks:
      - wpsite
  # Wordpress
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - '8000:80'
    restart: always
    volumes: ['./:/var/www/html']
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpresswordpress
      WORDPRESS_DB_NAME: wordpress
    networks:
      - wpsite
networks:
  wpsite:
volumes:
  db_data:
```
1. `db`: MySQL 5.7 이미지를 기반으로 하는 데이터베이스 서비스입니다. 환경 변수를 통해 root 비밀번호, 데이터베이스 이름, 사용자 이름, 사용자 비밀번호를 설정합니다. 데이터는 볼륨(db_data)에 저장되므로 컨테이너를 재시작해도 데이터가 유지됩니다.
2. `phpmyadmin` : phpMyAdmin 이미지를 기반으로 하는 서비스로, 데이터베이스 서비스(db)에 의존합니다. 8080 포트에서 실행되며, 데이터베이스 서비스에 연결하기 위한 환경 변수를 설정합니다.
3. `wordpress` : 최신 WordPress 이미지를 기반으로 하는 서비스로, 데이터베이스 서비스(db)에 의존합니다. 8000 포트에서 실행되며, 데이터베이스에 연결하기 위한 환경 변수를 설정합니다. 또한, 현재 디렉토리(./)를 WordPress의 `HTML 디렉토리(/var/www/html)`에 마운트합니다.

이 설정을 사용하면, 단일 명령(`docker-compose up`)으로 세 개의 서비스를 함께 시작할 수 있습니다. 이는 `웹 개발 및 테스팅에 유용한 환경을 제공합니다.`