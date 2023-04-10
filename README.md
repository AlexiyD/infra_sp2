# API REST для YaMDB
## Описание:
>Проект YaMDb собирает отзывы пользователей на произведения.
>Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка».
>Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
>Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). 
>Добавлять произведения, категории и жанры может только администратор.
>Пользователи могут оставлять "Отзывы" и ставят произведению оценку. Из оценок формируется рейтинг.

### Технологии:
* Python 3.8 
* Django 3.2.16
* Django REST framework 3.12.4
* PyJWT + Djoser 2.1.0
* Djangorestframework-simplejwt 4.8.0

## Как запустить проект:

### Клонировать репозиторий и перейти в него в командной строке:
* git clone 
https://github.com/Dmitriy573/api_yamdb.git

### Переходим в рабочую дерикторию:
* cd .../api_yamdb/

### Cоздать и активировать виртуальное окружение:
* python -m venv env
* source venv/Scripts/activate

### Установить зависимости из файла requirements.txt:
* python -m pip install --upgrade pip
* pip install -r requirements.txt

### Выполнить миграции:
* python manage.py makemigrations
* python manage.py migrate

### Запустить проект:
* python manage.py runserver

Полная документация прокта (redoc) доступна по адресу http://127.0.0.1:8000/redoc/

## Примеры запросов и ответов:
### Регистрация нового пользователя

#### Пример запроса
```URL
POST: http://127.0.0.1:8000/api/v1/auth/signup/
```
```JSON
{
    "email": "user@example.com",
    "username": "string"
}
```
#### Пример ответа
```JSON
{
    "email": "string",
    "username": "string"
}
```
### Получение JWT-токена
#### Пример запроса
```URL
POST: http://127.0.0.1:8000/api/v1/auth/token/
```
```JSON
{
    "username": "string",
    "confirmation_code": "string"
}
```
#### Пример ответа
```JSON
{
    "token": "string"
}
```

### Добавление произведения
#### Пример запроса
```URL
POST: http://127.0.0.1:8000/api/v1/titles/
```
```JSON
{
    "name": "string",
    "year": 0,
    "description": "string",
    "genre": [
        "string"
    ],
    "category": "string"
}
```
#### Пример ответа
```JSON
{
    "id": 0,
    "name": "string",
    "year": 0,
    "rating": 0,
    "description": "string",
    "genre": [
        {
            "name": "string",
            "slug": "string"
        }
    ],
    "category": {
        "name": "string",
        "slug": "string"
    }
}
```

### Добавление нового отзыва
#### Пример запроса
```URL
POST: http://127.0.0.1:8000/api/v1/titles/{title_id}/reviews/
```
```JSON
{
    "id": 0,
    "text": "string",
    "author": "string",
    "score": 1,
    "pub_date": "2019-08-24T14:15:22Z"
}
```
#### Пример ответа
```JSON
{
    "id": 0,
    "text": "string",
    "author": "string",
    "score": 1,
    "pub_date": "2019-08-24T14:15:22Z"
}
```

## Авторы:
* Дмитрий Потапкин - Dmitriy573 (Team Lead, разработчик) - Модели, view и эндпойнты, Категории, Жанры, Произведения,  импорт данных из csv файлов.
* Анастасия Карелина - Anastasiya3112 (разработчик) - управления пользователями: система регистрации и аутентификации, права доступа, Токены, система подтверждения через e-mail.
* Зубков Алексей - AlexiyD (разработчик) - Отзывы, комментарии, рейтинг произведений.
