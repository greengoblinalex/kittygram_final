<h1 align="center">Всем привет! Меня зовут <a href="https://github.com/greengoblinalex" target="_blank">Алексей</a> и я автор данного приложения
<img src="https://github.com/blackcater/blackcater/raw/main/images/Hi.gif" height="32"/></h1>

# Kittygram

## Описание

Проект Kittygram - это сервис с картинками котиков, который позволяет добавлять пользователям картинки своих котиков или просматривать чужих котиков. Котикам можно выбрать дату рождения, цвет, картинку и их достижения

## Развертывание проекта локально
*При развертывании проетка требуется установить Docker*

1. Переходим в главную дирректорию проекта Kittygram
2. Далее прописываем команду `docker compose up`
3. Выполняем миграции с помощью команды `docker compose exec backend python manage.py migrate`

## Развертывание проекта на сервере, с использованием CI/CD и отправкой сообщения об успешном деплое в Telegram

1. Сделайте Fork репозитория Kittygram
2. Зайдите в settings сфоркнутого репозитория и пропишите все Secrets:
DOCKER_PASSWORD - Пароль от dockerhub
DOCKER_USERNAME - Username от dockerhub
USER - username хоста
HOST - ip хоста
SSH_KEY - ssh-ключ хоста
SSH_PASSPHRASE - пароль хоста
TELEGRAM_TO - id вашего телеграма
TELEGRAM_TOKEN - токен вашего телеграм-бота
3. Создайте деррикторию kittygram на сервере
4. Скопируйте в данную деррикторию docker-compose.production.yml и .env(можно использовать .env.example, в нем нужно заменить данные на свои)
5. Теперь, при пуше коммита в ветку main, будет проходить автоматическое тестирование кода, обновление image в dockerhub, деплой всего на сервер с последующим перезапуском сети контейнеров


## <a href="https://simonov-tech.ru" target="_blank">Развернутый проект</a>