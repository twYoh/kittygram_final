# Kittygram

![CI/CD Status](https://github.com/twYoh/kittygram_final/actions/workflows/main.yml/badge.svg)

## О проекте

Kittygram — это веб-приложение, которое позволяет пользователям делиться фотографиями своих питомцев, добавлять описание и делиться эмоциями.  
Проект разработан с использованием современных технологий, включая автоматизацию развёртывания с помощью Docker и CI/CD через GitHub Actions.

## Стек технологий

- Python 3
- Django
- Docker
- PostgreSQL
- Nginx
- Gunicorn
- GitHub Actions (CI/CD)
- pytest (автотесты)

## Развёртывание проекта

### Локально без использования Docker

1. Клонируйте репозиторий и перейдите в папку проекта:

    ```bash
    git clone https://github.com/yandex-praktikum/kittygram_backend.git
    cd kittygram_backend
    ```

2. Создайте и активируйте виртуальное окружение:

    - Для Linux/macOS:

        ```bash
        python3 -m venv env
        source env/bin/activate
        ```

    - Для Windows:

        ```bash
        python3 -m venv env
        env\Scripts\activate
        ```

3. Установите зависимости:

    ```bash
    pip install -r requirements.txt
    ```

4. Выполните миграции:

    ```bash
    python3 manage.py migrate
    ```

5. Запустите сервер разработки:

    ```bash
    python3 manage.py runserver
    ```

### В контейнерах с Docker

1. Убедитесь, что Docker установлен на вашем устройстве.

2. Склонируйте репозиторий и перейдите в папку проекта:

    ```bash
    git clone https://github.com/yandex-praktikum/kittygram_backend.git
    cd kittygram_backend
    ```

3. Создайте файл `.env` в корне проекта и заполните его по примеру:

    ```env
    DEBUG=False
    SECRET_KEY=ваш_секретный_ключ
    POSTGRES_DB=kittygram
    POSTGRES_USER=ваш_пользователь
    POSTGRES_PASSWORD=ваш_пароль
    DB_HOST=db
    DB_PORT=5432
    ALLOWED_HOSTS=127.0.0.1,localhost
    ```

4. Соберите и запустите контейнеры:

    ```bash
    docker-compose up -d --build
    ```

5. Убедитесь, что проект доступен по адресу [http://localhost/](http://localhost/).  
   Если возникли проблемы, проверьте логи с помощью команды:

    ```bash
    docker-compose logs -f
    ```

## CI/CD с GitHub Actions

GitHub Actions автоматизирует процесс тестирования и деплоя.  
Пуш в ветку `main` запускает автотесты и развёртывание проекта.

### Настройка

1. Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корне проекта.

2. Создайте файл `tests.yml` и заполните его следующим образом:

    ```yaml
    repo_owner: ваш_логин_на_гитхабе
    kittygram_domain: https://доменное_имя_kittygram
    dockerhub_username: ваш_логин_на_докерхабе
    ```

3. Настройте webhook для получения уведомлений о статусе деплоя (например, в Telegram).  
   Для этого можно использовать такие сервисы, как BotFather для создания бота и настроить его в GitHub Actions.

## Автор

Разработано Yoh.  
Контактная информация для обратной связи:  
- GitHub: [github.com/twYoh](https://github.com/twYoh)  
- Email: yoh@asakuraking.ru
