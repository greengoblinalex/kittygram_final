<h1 align="center">Всем привет! Меня зовут <a href="https://github.com/greengoblinalex" target="_blank">Алексей</a> и я автор данного проекта
<img src="https://github.com/blackcater/blackcater/raw/main/images/Hi.gif" height="32"/></h1>

# Kittygram
![Deploy badge](https://github.com/greengoblinalex/kittygram_final/actions/workflows/main.yml/badge.svg)

## Описание

Проект Kittygram - это сервис с картинками котиков, который позволяет добавлять пользователям картинки своих котиков или просматривать чужих котиков. Котикам можно выбрать дату рождения, цвет, картинку и их достижения

## Развертывание проекта локально
*При развертывании проетка требуется установить Docker*

1. Переходим в главную дирректорию проекта kittygram
2. Добавляем в нее файл .env и прописываем в нем нужные данные, как в .env.example
3. Запускаем Docker Compose в режиме демона `sudo docker compose -f docker-compose.production.yml up -d`
4. Выполняем миграции с помощью команды `docker compose exec backend python manage.py migrate`

## Развертывание проекта на сервере
1. Устанавливаем Docker Compose на сервер
```
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin 
```
2. Устанавливаем и запускаем nginx
```
sudo apt install nginx
sudo systemctl start nginx
```
3. Через редактор Nano откройте файл конфигурации веб-сервера
```
sudo nano /etc/nginx/sites-enabled/default
```
4. Удалите все настройки из файла, запишите и сохраните новые
```
server {
    listen 80;
    server_name публичный_ip_вашего_удалённого_сервера;
    
    location / {
        proxy_set_header HOST $host;
        proxy_pass http://127.0.0.1:9000;
    }

} 
```
3. Создаём деррикторию kittygram на сервере
4. Копируем в данную деррикторию docker-compose.production.yml и создаём .env, после чего прописываем в нем нужные данные, как в .env.example
5. Запускаем Docker Compose в режиме демона 
```
sudo docker compose -f docker-compose.production.yml up -d
```
6. Выполняем миграции с помощью команды 
```
docker compose exec backend python manage.py migrate
```

## Развертывание проекта с использованием CI/CD
1. Делаем Fork репозитория Kittygram
2. Заходим в settings сфоркнутого репозитория и прописываем все Secrets:
DOCKER_PASSWORD - Пароль от dockerhub
DOCKER_USERNAME - Username от dockerhub
USER - username хоста
HOST - ip хоста
SSH_KEY - ssh-ключ хоста
SSH_PASSPHRASE - пароль хоста
TELEGRAM_TO - id вашего телеграма
TELEGRAM_TOKEN - токен вашего телеграм-бота
3. Устанавливаем Docker Compose на сервер
```
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin 
```
4. Устанавливаем и запускаем nginx
```
sudo apt install nginx
sudo systemctl start nginx
```
5. Через редактор Nano откройте файл конфигурации веб-сервера
```
sudo nano /etc/nginx/sites-enabled/default
```
6. Удалите все настройки из файла, запишите и сохраните новые
```
server {
    listen 80;
    server_name публичный_ip_вашего_удалённого_сервера;
    
    location / {
        proxy_set_header HOST $host;
        proxy_pass http://127.0.0.1:9000;
    }

} 
```
7. Создаём деррикторию kittygram на сервере
8. Копируем в данную деррикторию docker-compose.production.yml и создаём .env, после чего прописываем в нем нужные данные, как в .env.example
9. Запускаем Docker Compose в режиме демона 
```
sudo docker compose -f docker-compose.production.yml up -d
```
10. Выполняем миграции с помощью команды 
```
docker compose exec backend python manage.py migrate
```
11. Теперь при пуше коммитов в ветку main будет происходить автоматическое тестирование, обновление image на dockerhub и деплой проекта на сервер

## <a href="https://simonov-tech.ru" target="_blank">Развернутый проект</a>
