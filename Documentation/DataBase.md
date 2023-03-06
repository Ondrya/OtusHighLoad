Для выполнения задания рекомендуется использовать MySQL v5.7
Чтобы упростить запуск, установим Docker и возьмём ядро БД из образа, для тестирования нужно будет просто накатить dump на базу в контейнере.

```
docker run --name mysql574 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=root -d mysql:5.7.41
```

Имя контейнера
```
--name mysql574
```
Имя образа
```
mysql:5.7.41
```
Run as a detached container (ctrl + c won't stop the container)
```
-d
```
Port expose (external port on host machine : internal port of the container)
Нужно, чтобы подключиться с ПК к базе в контейнере
```
-p 3306:3306
```
Установка переменных окружения
```
-e MYSQL_ROOT_PASSWORD=root
-e MYSQL_DATABASE=testdb
-e MYSQL_USER=admin
-e MYSQL_PASSWORD=root
```

Для доступа к базе "глазами" скачаем MySQL [Workbench](https://dev.mysql.com/downloads/windows/installer/8.0.html)


### DUMP ###
В итоговом контейнере попробовать загрузить dump базы данных. Example:

```yaml
mysql:
 image: mysql:5.6
 environment:
   MYSQL_ROOT_PASSWORD: pass
 ports:
   - 3306:3306
 volumes:
   - ./db-dump:/docker-entrypoint-initdb.d
```
