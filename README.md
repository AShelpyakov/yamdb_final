![CI-CD workflow](https://github.com/AShelpyakov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# Учебный проект по работе c docker и docker-compose 
### Описание
Изучение работы Docker и Docker-Compose на основе предыдущего учебного
проекта API_YAMDB.
### Технологии
Python 3.7,
Django 2.2.28,
Djangorestframework 3.12.4,
Docker,
Docker-Compose
### Запуск проекта в dev-режиме
- Установить docker и docker-compose
- Создать .env файл в папке infra
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=password # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
SECRET_KEY=very_secret_key # SECRET_KEY для django
```
- Запустить docker-compose в папке infra
```
docker-compose up -d
```
- Произвести миграцию (опционально, при изменении в структуре базы данных или перовом запуске)
```
python manage.py migrate
```
- Создать административного пользователя (опционально, при первом запуске)
```
docker-compose exec web python manage.py createsuperuser
```
- Перенести статику в папку для NGINX (опционально, при первом запуске)
```
python manage.py collectstatic --no-input
```
- Внести тестовые дынные в базу(опционально, при первом запуске)
```
python manage.py loaddata fixtures.json &&
```

### Автор
Александр Шельпяков