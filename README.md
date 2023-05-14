### Проект YaMDb

![example workflow](https://github.com/atar1boy/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Сервис позволяющий пользователям оценивать и писать свои рецензии на любые категории творчества

## Команда разработчиков:
Самсонов Дмитрий
Никита Ковалев
Алексей Наумов

## Используемые технолологии:

Django v.3.2
djangorestframework v.3.12.4
PyJWT v.2.1.0

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:atar1boy/infra_sp2
```

Создать .env файл внутри директории infra (на одном уровне с docker-compose.yaml) Пример .env файла:

```
SECRET_KEY = 'p&l%385148kslhtyn^##a1)ilz@4zqj=rq&agdol^##zgl9(vs'
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

* Если у вас Linux/macOS

    ```
    source env/bin/activate
    ```

* Если у вас windows

    ```
    source env/scripts/activate
    ```

```
python3 -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Запуск Docker контейнеров: Запустите docker-compose:

```
cd infra/
docker-compose up -d --build
```

Выполните миграции:
```
docker-compose exec web python manage.py makemigrations reviews
docker-compose exec web python manage.py migrate
```

Cоздайте суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Подготовьте статику:

```
docker-compose exec web python manage.py collectstatic --no-input 
```

## Аунтификация токена:

Самостоятельная регистрация и подтверждение адреса электронной почты:

```
http://127.0.0.1:8000/api/v1/auth/signup/
```

Получить/обновить токен:

```
http://127.0.0.1:8000/api/v1/auth/token/
```

## Примеры запросов к Api:

Получение ревью по id тайтла.

```
http://127.0.0.1:8000/api/v1/titles/1/reviews/
```
Получение списка комментариев на ревью
```
http://127.0.0.1:8000/api/v1/titles/1/reviews/1/comments/
```

## Документация

```
http://localhost/redoc/
```