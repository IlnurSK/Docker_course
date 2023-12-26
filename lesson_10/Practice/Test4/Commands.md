# Команды для поднятия сайта локально

Чтобы команды сработали, нужно находиться в текущей папке (`lesson_7`).
Результатом команды ls должно быть что-то в таком роде:

```
backend  database  frontend  nginx  README.md  Сommands.md
```

## Создаем образы

```shell
docker build -t 7_back ./backend
```

```shell
docker build -t 7_database ./database
```

```shell
docker build -t 7_nginx ./frontend
```

## Создаем сеть и вольюм

```shell
docker volume create todo_db
```

```shell
docker network create todo_net
```

## Поднимаем базу данных

```shell
docker run --rm -d \
  --name database \
  --net=todo_net \
  -e POSTGRES_DB=123 \
  -e POSTGRES_USER=123 \
  -e POSTGRES_PASSWORD=123 \
  postgres
```

## Поднимаем бекенд

```shell
docker run --rm -d \
  --name backend \
  --net=todo_net \
  -e PG_HOST=database \
  -e PG_DATABASE=123 \
  -e PG_USER=123 \
  -e PG_PASSWORD=123 \
  kcoursedocker/task-7.4-back
```

## Поднимаем фронтедн

```shell
docker run --rm -d \
  --name frontend \
  --net=todo_net \
  -p 80:80 \
  kcoursedocker/task-7.4-front
```

## Заходим на сайт [http://localhost](http://localhost)

