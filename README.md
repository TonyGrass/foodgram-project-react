# foodgram

## Запуск локально с использованием docker-compose

### Шаблон наполнения env-файла:

Создайте файл .env с переменными окружения для работы с базой данных:

DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=* # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД 
SECRET_KEY=* # секретный ключ
DEBUG='True' # включить/выключить режим debug

### Как запустить проект в контейнерах:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/TonyGrass/foodgram-project-react.git
```

```
cd foodgram-project-react/infra/
```

Собрать образ и контейнеры:

```
sudo docker-compose up -d --build
```

Создать миграции:
```
sudo docker-compose exec backend python manage.py makemigrations
```

Выполнить миграции:

```
sudo docker-compose exec backend python manage.py migrate
```

Создать суперюзера:

```
sudo docker-compose exec backend python manage.py createsuperuser
```

Собрать статику:

```
sudo docker-compose exec backend python manage.py collectstatic --no-input
```

### Команда для заполнения БД:

Выполните команду находясь в директории с файлом manage.py:

```
sudo docker-compose exec backend python manage.py load_tags
```

```
sudo docker-compose exec backend python manage.py load_ingrs
```

### Документация и примеры запросов доступны по адресу:

```
http://127.0.0.1/redoc/
```
