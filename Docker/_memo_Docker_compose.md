
# docker-compose
## docker-compose info
* link : 도커 컴포즈를 활용하여 완벽한 개발 환경 구성하기 (컨테이너 시대의 Django 개발환경 구축하기) : https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose
## Install on linux
```
curl -SL https://github.com/docker/compose/releases/download/v2.17.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose  # chmod 를 통해서 실행이 가능하게 세팅
docker-compose -v # docker-compose 명령이 제대로 먹히는 지 확인한다.
```
## Command
### up
```
docker-compose up -d
```
* -d: 서비스 실행 후 콘솔로 빠져나옵니다. (docker run에서의 -d와 같습니다.)
* --force-recreate: 컨테이너를 지우고 새로 만듭니다.
* --build: 서비스 시작 전 이미지를 새로 만듭니다.

### rm
```
docker-compose rm -f
```

### down
* --volume: 볼륨까지 삭제합니다.

## Examples
* Example1
```
services:
  container1:
    command:
      - python manage.py runserver 0:8000
```

* Example2
```
services:
  container2:
    command:
      - bash
      - -c
      - |
        /wait-for-it.sh db:5432 -t 10
        python manage.py runserver 0:8000
```        
## Example 3
```
mkdir html
echo "<h1>hi</h1>" > html/index.html
echo "
version: '3'

services:
  t1:
    image: nginx
    volumes:
      - ./html:/usr/share/nginx/html/
    ports:
      - 8888:80
    restart: always
">docker-compose.yml
docker-compose up -d
open http://127.0.0.1:8888
```

## Example 4
```
echo "
version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - /Users/nowage/work-etc/docker/db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
" > docker-compose.yml

```
open http://127.0.0.1:8000
