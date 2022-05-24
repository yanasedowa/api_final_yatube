# API для Yatube
### Описание
**API** (от англ. **A**pplication **P**rogramming **I**nterface, «программный интерфейс приложения») — это интерфейс для обмена данными.
**api_final_yatube** — это финальный проект Django REST framework, состоящий из приложений **Posts** и **API**. Приложение Posts включает модели для создания БД. Приложение API включает urlpatterns, views (ModelViewSet), serializers. Основной функционал API проекта api_final_yatube:
> -   использование JWT-токенов для аутенфикации пользователей;
> -   получение, создание, обновление и удаление поста/постов с разрешением IsAuthenticatedOrReadOnly (получение списка постов, разделенных на страницы с помощью LimitOffsetPagination);
> -   получение, создание, обновление и удаление комментария/комментариев к посту с разрешением IsAuthenticatedOrReadOnly;
> -   просмотр группы/групп с разрешением IsAuthenticatedOrReadOnly;
> -   чтобы подписаться на пользователя, получить список подписчиков и выполнить поиск по имени подписки с разрешением IsAuthenticated.
### Как запустить проект:

  

Клонировать репозиторий и перейти в него в командной строке:

  

```

git clone https://github.com/# **yandex-praktikum/api_final_yatube.git

```

  

```

api_final_yatube

```

  

Cоздать и активировать виртуальное окружение:

  

```

python3 -m venv env

```

  

Для *nix-систем:

```

source venv/bin/activate

```

Для windows-систем:

```

source venv/Scripts/activate

```
  

```

python3 -m pip install --upgrade pip

```

  

Установить зависимости из файла requirements.txt:

  

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

Документация к проекту:

http://127.0.0.1:8000/redoc


### Примеры запросов:

Получить список всех публикаций. При указании параметров limit и offset выдача должна работать с пагинацией. 

**GET**
/api/v1/posts/

*Ответ*
**200**
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```
Обновление публикации по id. Обновить публикацию может только автор публикации. Анонимные запросы запрещены.

**PUT**
/api/v1/posts/{id}/

*Передаваемые данные*

```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```

*Ответ*
**200**
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```

*Ответ*
**401**
```
{
  "detail": "Учетные данные не были предоставлены."
}
```
Подписка пользователя от имени которого сделан запрос на пользователя переданного в теле запроса. Анонимные запросы запрещены.

**PUT**
/api/v1/follow/
*Передаваемые данные*
```
{
  "following": "string"
}
```

*Ответ*
**200**
```
{
  "user": "string",
  "following": "string"
}
```

*Ответ*
**400**
```
{
  "following": [
    "Обязательное поле."
  ]
}
```

### Технологии

-   [Python](https://www.python.org/)
-   [Django](https://www.djangoproject.com/)
-   [Django REST framework](https://www.django-rest-framework.org/)
-   [DRF Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)

### Автор
Седова Яна, 33 когорта 
