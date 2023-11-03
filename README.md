<h1 align="center">Социальная сеть <a href="https://prettycat.ddns.net/" target="_blank">Kittygram.</a></h1>

  В нашей социальной сети вы можете создать аккаунт для вашего любимого котика, чтобы все, кто заходит в kittigram, могли посмотреть его страничку.
На странице вашего котика вы можете разместить его фотографию, выбрать окрас любимца и рассказать какие у вашего питомца есть достижения.

## Деплой проекта Kittygram на удалённый сервер.
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![Gunicorn](https://img.shields.io/badge/gunicorn-%298729.svg?style=for-the-badge&logo=gunicorn&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)

### Инструкция для установки проекта с репозитория на ваш локальный компьютер:

1. Склонируйте репозиторий, выполнив команду `git clone <адрес вашего репозитория>`. Это создаст локальную копию проекта на вашем компьютере.

2. Перейдите в директорию с клонированным репозиторием. Вы можете использовать команду `cd <директория>`, чтобы перейти к нужной директории.

3. Создайте виртуальное окружение для проекта, выполните команду `python3 -m venv venv`. Виртуальное окружение позволяет изолировать зависимости проекта от других проектов на вашем компьютере.

4. Установите все необходимые зависимости проекта, выполните команду `pip install -r requirements.txt`. Файл `requirements.txt` содержит список всех зависимостей проекта, которые будут установлены.

5. В директории `/backend/kittygram_backend/` создайте файл `.env`. Этот файл будет содержать конфиденциальную информацию, такую как секретный ключ.

6. Откройте файл `.env` и пропишите ваш секретный ключ в формате: `SECRET_KEY=<ваш_ключ>`, список разрешенных хостов `ALLOWED_HOST=127.0.0.1, <your_domain>` и переменную `DEBUG=True`

_После выполнения этих шагов вы успешно установите проект на ваш локальный компьютер и будете готовы к его использованию и дальнейшей разработке._
