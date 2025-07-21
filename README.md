# Kittygram

**Kittygram** — веб-приложение для публикации и просмотра фотографий котиков. Позволяет пользователям регистрироваться, добавлять посты с изображениями котиков.

## Установка и запуск

1. Клонирование репозитория:

   ```bash
   git clone https://github.com/<ваш_логин>/kittygram_final.git
   cd kittygram_final
   ```
2. Запуск проекта в контейнерах:

   ```bash
   docker compose -f docker-compose.production.yml up -d --build
   ```
3. Выполнение миграций и сбор статики:

   ```bash
   docker compose exec backend python manage.py migrate
   docker compose exec backend python manage.py collectstatic --noinput
   ```

## Примеры запросов

Базовый URL: `https://<ваш_домен>/api/`

* **Получить список постов**

  ```http
  GET /api/posts/ HTTP/1.1
  Host: <ваш_домен>
  Authorization: Token <ваш_token>
  ```
* **Создать новый пост**

  ```http
  POST /api/posts/ HTTP/1.1
  Host: <ваш_домен>
  Authorization: Token <ваш_token>
  Content-Type: application/json

  {
    "title": "Мой котик",
    "image": "data:image/png;base64,..."
  }
  ```
* **Получить данные текущего пользователя**

  ```http
  GET /api/users/me/ HTTP/1.1
  Host: <ваш_домен>
  Authorization: Token <ваш_token>
  ```

## Используемые технологии

* Python 3.9
* Django 3.2
* Django REST Framework
* PostgreSQL 13
* Docker
* Docker Compose
* NGINX
* React
* GitHub Actions

## Автор

Дмитрий Шибаев
GitHub: [https://github.com/dimash1baev](https://github.com/dimashibaev)


#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.
