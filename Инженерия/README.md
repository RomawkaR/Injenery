## Проект «API для Yatube»

«API для Yatube» расширяет возможности социальной сети - "Yatube". Пользователи могут публиковать свои посты и управлять подписками через программный интерфейс взаимодействия, а также смотреть сообщества и оставлять комментарии к постам.

### Технологии

- [Python](https://www.python.org/) - язык программирования.
- [Django](https://www.djangoproject.com/) - свободный фреймворк для веб-приложений на языке Python.
- [Django REST Framework](https://www.django-rest-framework.org/) - мощный и гибкий набор инструментов для создания веб-API.
- [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/) - плагин аутентификации JSON Web Token для Django REST Framework.

### Как запустить проект:

Клонировать репозиторий и перейти в него в консоле:

`git clone https://github.com/romawkar/api_final_yatube.git`

`cd api_final_yatube`


Создать и активировать виртуальное окружение:

+ `python3 -m venv env`
+ `. venv/scripts/activate`

Установить зависимости из файла requirements.txt:
`pip install -r requirements.txt`

Выполнить миграции:
+ `cd yatube_api`
+ `python3 manage.py makemigrations`
+ `python3 manage.py migrate`

Запустить проект:
`python3 manage.py runserver`

Документация проекта:
`http://localhost:port/redoc/`

#### Примеры запросов:

POST-запрос с токеном, добавление новой публикации в коллекцию публикаций.

`POST http://localhost:port/api/v1/posts/`

```
{
  "text": "Сегодня прзднуется день города - Павлово! Все идем на концерт на центральной площади к 21:00!",
  "group": 1
}
```

Ответ:

```
{
    "id": 1,
    "author": "Dante",
    "text": "Сегодня прзднуется день города - Павлово! Все идем на концерт на центральной площади к 21:00!",
    "pub_date": "2023-07-14T02:37:44.494905Z",
    "image": null,
    "group": 1
}
```


GET-запрос, получение информации о сообществе по id=1.

`GET http://localhost:port/api/v1/groups/1/`

Ответ:

```
{
    "id": 1,
    "title": "Crew",
    "slug": "crew-group",
    "description": "blizkie"
}
```

POST-запрос, подписка авторизованного пользователя `Dante` от имени которого сделан запрос на автора интересующей публикации `Leo`.

`POST http://localhost:port/api/v1/follow/`

```
{
  "following": "Leo"
}
```

Ответ:

```
{
    "id": 2,
    "user": "Dante",
    "following": "Leo"
}
```

#### Автор проекта:
Родионов Роман