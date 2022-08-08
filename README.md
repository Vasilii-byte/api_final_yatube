# API-интерфейс для проекта Yatube

## О проекте
В программе с помощью Django REST Framework реализован REST API-интерфейс для Yatube.

Проект Yatube реализует упрощенный и легковесный, но в то же время мощный интернет-дневник (блог), в котором предусмотрены:
+ система авторизации пользователей;
+ создание тематических сообществ;
+ создание и редактирование публикаций;
+ возможность комментирования публикаций;
+ возможность подписки на интересующих авторов (для авторизованных пользователей).

## Технологии, используемые в проекте
- [Python], v3.8. Python is a programming language that lets you work quickly and integrate systems more effectively.
- [Django], v2.2.16. DjangoThe web framework for perfectionists with deadlines.
- [Django REST framework], v3.12.4. Django REST framework is a powerful and flexible toolkit for building Web APIs.
- [JWT], v4.7.2. JSON Web Tokens are an open, industry standard RFC 7519 method for representing claims securely between two parties.
- [Pillow], v8.3.1. The Python Imaging Library adds image processing capabilities to your Python interpreter.

## Возможности API-интерфейса
У неавторизованных пользователей имеется доступ к API только на чтение, а список подписок недоступен.

Для авторизованных пользователей имеется возможность создавать публикации, комментарии, подписываться на авторов и редактировать свои материалы.

С API-интерфейсом можно ознакомиться по адресу `/redoc/` после запуска сервера.

Некоторые примеры API-запросов:
+ для доступа к API-интерфейсу необходимо получить JWT-токен. Для этого нужно отправить POST-запрос на адрес `/api/v1/jwt/create/`.
В теле запроса нужно передать JSON: 
```
{
  "username": "string",
  "password": "string"
}
```
Ответом будет JSON-словарь с токенами:
```
{
  "refresh": "string",
  "access": "string"
}
```
Далее в заголовке `Header` нужно передавать параметр `Bearer <token>`.

+ для получения списка публикаций формируем `GET`-запрос `/api/v1/posts/`.
Пример ответа на запрос: 
```
  [
      {
          "id": 1,
          "author": "vasiliy",
          "text": "Знания умножают скорбь.",
          "pub_date": "2022-08-02T18:52:57.958136Z",
          "image": null,
          "group": null
      },
      {
          "id": 5,
          "author": "testuser1",
          "text": "Yet another post",
          "pub_date": "2022-08-06T10:46:07.004521Z",
          "image": null,
          "group": null
      }
  ]
```
+ для создания новой публикации формируем `POST`-запрос `/api/v1/posts/`.
`Body` запроса: 
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
+ получение списка комментариев: `GET`-запрос `/api/v1/posts/{post_id}/comments/`.
Пример ответа на запрос: 
```
[
  {
    "id": 0,
    "author": "Decart",
    "text": "Cogito ergo sum",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
  }
]
```
+ удаление поста: `DELETE`-запрос `/api/v1/posts/{id}/`

## Как запустить проект:

Клонировать репозиторий так:

```sh
git clone https://github.com/Vasilii-byte/api_final_yatube.git
```
или вот так:
```sh
git clone git@github.com:Vasilii-byte/api_final_yatube.git
```

Перейти в папку проекта в командной строке:
```sh
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```sh
python3 -m venv env

source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```sh
python3 -m pip install --upgrade pip

pip install -r requirements.txt
```

Выполнить миграции:

```sh
python3 manage.py migrate
```

Запустить проект:

```sh
python3 manage.py runserver
```

## Hi there 👋, my name is Vasilii

I made this project as part of a training project at Yandex.Practikum. It was interesting.

Skills: Python / Django

- 🔭 I’m currently working on this page. 
- 👯 I’m looking to collaborate on projects with Python & Django

[<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg' alt='github' height='40'>](https://github.com/https://github.com/Vasilii-byte)  [<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg' alt='linkedin' height='40'>](https://www.linkedin.com/in/https://www.linkedin.com/in/василий-глушков-11250765//)    

[//]: # 
  [Python]: <https://www.python.org>
  [Django REST framework]: <https://www.django-rest-framework.org>
  [Django]: <https://www.djangoproject.com>
  [JWT]: <https://jwt.io>
  [Pillow]: <https://pillow.readthedocs.io/>