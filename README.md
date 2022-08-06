## API-интерфейс для проекта Yatube

В программе с помощью Django REST Framework реализован REST API-интерфейс для Yatube.

У неавторизованных пользователей имеется доступ только на чтение, а список подписок недоступен.

Для авторизованных пользователей имеется возможность создавать публикации, комментарии, подписываться на авторов и редактировать свои материалы.

### Как запустить проект:

Клонировать репозиторий так:

```
git clone https://github.com/Vasilii-byte/api_final_yatube.git
```
или вот так:
```
git clone git@github.com:Vasilii-byte/api_final_yatube.git
```

Перейти в папку проекта в командной строке
```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

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
