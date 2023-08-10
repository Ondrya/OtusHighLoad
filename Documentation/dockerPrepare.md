Создадим сеть
```
docker network create -d bridge otus
```

Контейнер с базой данных
```
docker run --net=otus --name mysql574 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=db -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -d mysql:5.7.41 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

Контейнер с PhpMyadmin
```
docker run --name phpmyadmin -d --link mysql574:db -p 8080:80 --net=otus phpmyadmin
```
