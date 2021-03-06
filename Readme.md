# Заготовка проекта Django

*стандартный Django с набором библиотек для быстрого старта проекта*


## Библиотеки в составе проекта

- [environs](https://pypi.org/project/environs/) - для организации работы с переменными окружения;
- [dj-database-url](https://pypi.org/project/dj-database-url/) - для компактной записи данных для подключения к БД в виде URL (см. ниже образец файла .env);
- [whitenoise](http://whitenoise.evans.io/en/stable/) - упрощение работы со статикой;
- [Debug-toolbar](https://pypi.org/project/django-debug-toolbar/) - отладка, мониторинг запросов к БД; 
- [Django-Jazzmin](https://django-jazzmin.readthedocs.io/) - тема для административной части сайта с дополнительным фунционалом;

## Настройки
Настройки для часовой зоны Мск.

    LANGUAGE_CODE = 'ru-RU'
    TIME_ZONE = 'Europe/Moscow'

## Кастомная модель пользователя

Устанавливается кастомная модель пользователя

*settings.py*

    AUTH_USER_MODEL = 'accounts.User'

*accounts: models.py*

    class User(AbstractUser):
        pass

## Приложения (apps)

Установлено приложение *accounts* с кастомной моделью пользователя.

## Шаблон

Установлен шаблон Bootstrap Carousel.

## Как установить

Код является свободным, ты можешь установить его и пользоваться. Для этого тебе понадобится:

1. Установить Python 3.10+. [см. как установить (англ.)](https://realpython.com/installing-python/), а [здесь для Debian-based (рус.)](http://userone.ru/?q=node/41).

2. Установить переменные окружения (см. ниже).


Далее, скачай репозиторий к себе, установи и активируй виртуальное окружение:
```
    python3 -m venv env
    source env/bin/activate
```
установи необходимые библиотеки, указанные в файле requirements.txt:
```
    pip install -r requirements.txt
```
перейди в папку проекта, запусти миграции, затем проект:
```
    ./manage.py migrate
    ./manage.py runserver
```

Открой браузер и укажи в адресной строке:
```
http://127.0.0.1:8000
```
чтобы попасть на главную страницу сайта, или
```
http://127.0.0.1:8000/admin/
```
для доступа к административной части сайта.

## Переменные окружения

Для улучшения уровня безопасности, когда будешь размещать сайт в общем доступе, сделай файл *.env* и размести его в папке настроек проекта *project*. В этом файле укажи:

* секретный ключ Django;
* данные для подключения к БД
* DEBUG и ALLOWED_HOSTS
* настройки почтового сервера


Вот так должен выглядеть твой .env файл:

    SECRET_KEY='длинная строка символов'
    DEBUG=False
    ALLOWED_HOSTS=127.0.0.1,[::1]
    DB_URL=postgres://user_name:password@host:port/db_name


если используется рассылка email, то потребуются данные почтового сервера:

    EMAIL_HOST='<smtp-server>'
    EMAIL_PORT=<port>
    EMAIL_USE_SSL=True
    EMAIL_HOST_PASSWORD='<password>'
    EMAIL_HOST_USER='<login name>'
    DEFAULT_FROM_EMAIL='<from email>'


Указывать эти ключи в файле настроек settings.py не нужно.
