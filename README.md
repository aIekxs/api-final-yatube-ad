# API Yatube

API для публикации постов, комментариев и подписок на авторов.

## Возможности

- Публикация постов
- Комментирование постов
- Создание групп
- Подписка на авторов
- JWT-аутентификация

## Технологии

- Python 3.11 (рекомендуемая версия)
- Django 3.2.16
- Django REST framework 3.12.4
- Djoser 2.1.0
- djangorestframework-simplejwt 4.7.2
- django-filter 2.4.0
- Pillow 9.3.0
- PyJWT 2.1.0
- python-dotenv 1.0.1

Полный список зависимостей и их версий находится в `requirements.txt`.

## Основные эндпоинты

| Метод | Эндпоинт | Описание |
|-------|----------|----------|
| POST | `/api/v1/auth/jwt/create/` | Получение JWT-токена |
| GET | `/api/v1/posts/` | Список постов |
| POST | `/api/v1/posts/` | Создать пост |
| GET | `/api/v1/posts/{id}/` | Пост по id |
| PUT/PATCH | `/api/v1/posts/{id}/` | Обновить пост (автор) |
| DELETE | `/api/v1/posts/{id}/` | Удалить пост (автор) |
| GET/POST | `/api/v1/posts/{post_id}/comments/` | Комментарии поста |
| GET/PUT/PATCH/DELETE | `/api/v1/posts/{post_id}/comments/{id}/` | Комментарий |
| GET | `/api/v1/groups/` | Список групп |
| GET | `/api/v1/groups/{id}/` | Группа по id |
| GET/POST | `/api/v1/follow/` | Подписки |
| GET | `/redoc/` | Документация API |

## Права доступа

- Все эндпоинты требуют JWT-токен (кроме `redoc`)
- Изменение/удаление постов и комментариев - только автору
- Подписки — только для авторизованных

## Запуск проекта

### 1. Клонирование репозитория

**Linux/macOS:**

```bash
git clone (ключ)
cd api-final-yatube-ad
```

**Windows (Git Bash):**

```bash
git clone (ключ)
cd api-final-yatube-ad
```

### 2. Создание виртуального окружения

**Linux/macOS:**

```bash
python3.11 -m venv venv
```

**Windows (Git Bash):**

```bash
python -m venv venv
```

### 3. Активация виртуального окружения

**Linux/macOS:**

```bash
source venv/bin/activate
```

**Windows (Git Bash):**

```bash
source venv/Scripts/activate
```

### 4. Установка зависимостей

**Linux/macOS:**

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

**Windows (Git Bash):**

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### 5. Настройка переменных окружения

Создайте файл `yatube_api/.env` из примера `yatube_api/.env_example`.

**Linux/macOS:**

```bash
cp yatube_api/.env_example yatube_api/.env
```

**Windows (Git Bash):**

```bash
cp yatube_api/.env_example yatube_api/.env
```

Затем откройте `yatube_api/.env` и укажите свои значения. Сгенерировать секретный ключ Django можно командой ниже (она одинакова для Linux/macOS и Windows Git Bash; окружение должно быть активировано):

```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

| Переменная | Назначение |
|---|---|
| `DJANGO_SECRET_KEY` | Секретный ключ Django для подписи cookie и токенов. Используйте уникальное значение; его можно сгенерировать командой выше. |
| `DJANGO_DEBUG` | Режим отладки. Установите `True` во время разработки. |
| `DJANGO_ALLOWED_HOSTS` | Разрешённые адреса, с которых можно обращаться к сайту. Несколько значений указываются через запятую. |

Проект использует SQLite; дополнительных переменных для подключения к базе данных не требуется.

### 6. Выполнение миграций

Сначала перейдите в каталог Django-проекта:

```bash
cd yatube_api
```

**Linux/macOS:**

```bash
python manage.py migrate
```

**Windows (Git Bash):**

```bash
python manage.py migrate
```

### 7. Запуск сервера

**Linux/macOS:**

```bash
python manage.py runserver
```

**Windows (Git Bash):**

```bash
python manage.py runserver
```
