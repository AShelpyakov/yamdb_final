![CI-CD workflow](https://github.com/AShelpyakov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# Учебный проект по созданию CI-CD на основе API_YAMDB 
### Описание
Изучение CI-CD на основе предыдущего учебного проекта API_YAMDB.
### Технологии
Python 3.7,
Django 2.2.28,
Djangorestframework 3.12.4,
Docker,
Docker-Compose,
Docker Hub,
GitHub.
### Запуск проекта
- Склонировать репозиторий на GitHub 
- Установить docker и docker-compose, на linux систему
- Скопировать файлы docker-compose.yaml и nginx/default.conf из вашего проекта на сервер в home/<ваш_username>/docker-compose.yaml и home/<ваш_username>/nginx/default.conf соответственно.
- Заполнить в GitHub secrets следующие параметры:
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=password # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
SECRET_KEY=very_secret_key # SECRET_KEY для django
DOCKERHUB_USERNAME=user # ваше имя в Docker Hub
DOCKERHUB_TOKEN=djeidfdkddfldf # ваш токен доступа с Docker Hub
HOST, USER, SSH_KEY # параметры для доступа к серверу с docker и docker-compose
TELEGRAM_TO=39495235 # ваш telegram id
TELEGRAM_TOKEN=jdsdsfsf:dsfjenjdskdfjdf # токен вашего телеграм бота
```
- Для запуска CI-CD, изменить что-то в проекте и отправить изменения на GitHub
- Произвести миграцию на сервере с Docker (опционально, при изменении в структуре базы данных или перовом запуске)
```
docker-compose exec web python manage.py migrate
```
- Создать административного пользователя (опционально, при первом запуске)
```
docker-compose exec web python manage.py createsuperuser
```
- Перенести статику в папку для NGINX (опционально, при первом запуске)
```
docker-compose exec web python manage.py collectstatic --no-input
```
### Автор
Александр Шельпяков