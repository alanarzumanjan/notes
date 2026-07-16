### Управление образами

- `docker images` – Список всех локальных образов.
- `docker pull <image>` – Загрузить образ из Docker Hub или другого реестра.
- `docker build -t <name> .` – Собрать образ из Dockerfile с присвоением имени.
- `docker rmi <image>` – Удалить локальный образ.
### Информация и отладка

- `docker info` – Общая информация о Docker.
- `docker inspect <container|image>` – Подробная информация о контейнере или образе.
- `docker version` – Версия Docker.

### Управление контейнерами

- `docker ps` – Список запущенных контейнеров.
- `docker ps -a` – Список всех контейнеров (запущенных и остановленных).
- `docker run <image>` – Запустить контейнер на основе образа.
- `docker run -it <image>` – Запустить контейнер в интерактивном режиме.
- `docker run -d <image>` – Запустить контейнер в фоновом режиме.
- `docker stop <container>` – Остановить работающий контейнер.
- `docker start <container>` – Запустить остановленный контейнер.
- `docker restart <container>` – Перезапустить контейнер.
- `docker rm <container>` – Удалить остановленный контейнер.

### Управление томами

- `docker volume ls` – Список доступных томов.
- `docker volume create <name>` – Создать новый том.
- `docker volume rm <name>` – Удалить том.
- `docker volume inspect <name>` – Информация о томе.

### Логи и мониторинг

- `docker logs <container>` – Показать логи контейнера.
- `docker stats` – Показать статистику ресурсов для работающих контейнеров.
- `docker top <container>` – Список процессов внутри контейнера.

### Очистка системы

- `docker system prune` – Удалить неиспользуемые контейнеры, образы, тома и сети.
- `docker system df` – Показать использование дискового пространства Docker.

### Управление сетями

- `docker network ls` – Список доступных сетей Docker.
- `docker network create <name>` – Создать новую сеть.
- `docker network rm <name>` – Удалить сеть.
- `docker network connect <network> <container>` – Подключить контейнер к сети.
- `docker network disconnect <network> <container>` – Отключить контейнер от сети.

```bash
docker build -t <image name> .
```

```bash
docker run -p 80:80 <image id>
```
### Docker push

```bash
docker login
docker tag local_image alaner/repo-name:latest
docker push alaner/repo-name:latest
```
### Docker pull
```docker
docker pull alaner/repo-name:latest
docker run alaner/repo_name
```

Подключиться с host к базе контейнера
#### Зайти в psql внутри контейнера
```shell
docker exec -it whiternet_postgres psql -U alan -d whiternet
```

####  Или выполнить одну команду
```shell
docker exec whiternet_postgres psql -U alan -d whiternet -c "SELECT count(*) FROM \"Subscribers\";"
```
