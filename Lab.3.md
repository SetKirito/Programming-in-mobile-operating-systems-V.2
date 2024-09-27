### Отчет по выполнению лабораторной работы №3: Network, Registry, Portainer (Строго по практическим шагам)

## Цель
Освоить базовые операции управления контейнерами Docker, а также развернуть Docker Registry, Shipyard и настроить лимиты на контейнер Apache.

## Шаги выполнения

### 1. Остановка всех контейнеров, кроме Portainer
Я использовал команду, чтобы остановить все контейнеры:
```bash
docker stop $(docker ps -a -q)
```
Для исключения контейнера Portainer я нашел его ID командой:
```bash
docker ps
```
После этого я остановил все, кроме Portainer.

### 2. Удаление всех контейнеров
Удалил все остановленные контейнеры:
```bash
docker container rm $(docker ps -a -q)
```

### 3. Удаление всех образов
Удалил все образы Docker:
```bash
docker image prune -a
```

### 4. Удаление всех томов
Удалил все диски (volumes):
```bash
docker volume rm $(docker volume ls -q)
```

### 5. Полная очистка системы Docker
Очистил систему Docker, удалив остановленные контейнеры и неиспользуемые образы:
```bash
docker system prune -a
```

### 6. Установка Docker Registry
Я установил Docker Registry с использованием официального образа:
```bash
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

### 7. Установка Shipyard и подключение к API Docker
Установил Shipyard для управления контейнерами и подключил его к Docker API:
```bash
docker run -d --name shipyard --link registry:registry -v /var/run/docker.sock:/var/run/docker.sock shipyard/shipyard
```
Затем подключился к интерфейсу Shipyard через веб-браузер и настроил управление.

### 8. Установка лимита на контейнер Apache
Запустил контейнер Apache и установил лимит на количество открытых файлов:
```bash
docker run -d -p 80:80 --name my-apache httpd:latest
docker exec -it my-apache /bin/bash
ulimit -n 1024
```
Теперь лимит на открытые файлы установлен в 1024.
