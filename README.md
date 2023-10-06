# Проект API
## Описание
Создание API для проекта на основе документации представленной в формате Redoc.

С помощью API можно работать с проектом без посещения сайта.

## Технологии
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) 
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) 

- [Python 3.9](https://www.python.org/downloads/)
- [Django 3.2.3](https://www.djangoproject.com/download/)
- [Django REST framework 3.12.4](https://pypi.org/project/djangorestframework/#files)
- [Djoser 2.1.0](https://djoser.readthedocs.io/en/latest/)
- [Simple JWT 4.7.2](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)

## Функционал

- Создание пользователя и его аутентификация.
- Подписка и отписка от автора.
- Просмотр, создание и удаление комментариев к публикации.
- Просмотр сообществ.

## Установка

1. Клонировать репозиторий:
```python
git clone
```
2. Перейти в папку с проектом:

   ```python
   cd api_final_yatube
   ```

3. Установить виртуальное окружение для проекта:

   ```python
   python -m venv venv
   ```

4. Активировать виртуальное окружение для проекта:

   ```python
   # для OS Lunix и MacOS
   source venv/bin/activate

   # для OS Windows
   source venv/Scripts/activate
   ```

5. Установить зависимости:

   ```python
   python3 -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

6. Выполнить миграции на уровне проекта:

   ```python
   cd yatube_api
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

7. Запустить проект:

   ```python manage.py runserver```

## Примеры запросов

***Получение токена***

Отправить POST-запрос на адрес `api/v1/jwt/create/` и передать 2 поля в `data`:

1. `username` - имя пользователя.
2. `password` - пароль пользователя.

***Создание поста***

Отправить POST-запрос на адрес `api/v1/posts/` и передать обязательное поле `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "text": "Проба пера, первый пост."
   }
   ```
   
2. Пример ответ:

   ```json
   {
     "id": 2,
     "author": "Test",
     "text": "Проба пера, первый пост.",
     "pub_date": "2022-04-22T16:00:22.021094Z",
     "image": null,
     "group": null
   }
   ```
***Комментирование поста пользователя***

Отправить POST-запрос на адрес `api/v1/posts/{post_id}/comments/` и передать обязательные поля `post` и `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "post": 1,
     "text": "Комментируем пост"
   }
   ```
2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "Dmitrii",
     "text": "Комментируем пост",
     "created": "2022-04-22T16:10:10.021094Z",
     "post": 1
   }
   ```

***Поучение списка всех постов***

Отправить GET-запрос на адрес `api/v1/posts/`

***Получениие определенного поста***

Отправить GET-запрос на адрес `api/v1/posts/1/`

***Получение списка всех групп***

Отправить GET-запрос на адрес `api/v1/groups/`


## Ресурсы
Документация проекта
```
http://127.0.0.1:8000/redoc/
```

## Автор
Кузнецов Юрий [GitHub](https://github.com/yvk3)
