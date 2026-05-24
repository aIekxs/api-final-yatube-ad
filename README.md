## Проект API-Yatube

Это учебный проект реализованный в рамках прохождения курса яндекс практикума бэкэнд на python.

### Возможности

- Публикация постов
- Комментирование постов
- Создание групп
- Подписка на авторов
- JWT-аутентификация

### Основные эндпоинты

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

### Права доступа

- Все эндпоинты требуют JWT-токен (кроме `redoc`)
- Изменение/удаление постов и комментариев - только автору
- Подписки — только для авторизованных

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/yandex-praktikum/kittygram.git
```

```
cd kittygram
```

Cоздать и активировать виртуальное окружение (для Linux):

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```