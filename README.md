<h1 align="center">Социальная сеть <a href="https://prettycat.ddns.net/" target="_blank">Kittygram.</a></h1>

  В нашей социальной сети вы можете создать аккаунт для вашего любимого котика, чтобы все, кто заходит в kittigram, могли посмотреть его страничку.
На странице вашего котика вы можете разместить его фотографию, выбрать окрас любимца и рассказать какие у вашего питомца есть достижения.

# Проект Kittygram.
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

## Деплой проекта на удаленный сервер

1. Убедитесь, что на вашем сервере установлен Git. Для проверки выполните команду `sudo apt update` и `git --version`. Если Git не установлен, установите его с помощью команды `sudo apt install git`.

2. На сервере сгенерируйте пару SSH-ключей с помощью команды `ssh-keygen`. Ключи будут сохранены в директории `.ssh`.

3. Сохраните открытый ключ в вашем аккаунте на GitHub. Для этого выполните команду `cat .ssh/id_rsa.pub` в терминале сервера, скопируйте вывод от символов `ssh-rsa` включительно до конца и добавьте его в настройках аккаунта на GitHub.

4. Склонируйте проект с GitHub на сервер командой `git clone git@github.com:Ваш_аккаунт/<Имя проекта>.git`.

## Для запуска бэкенд-приложения нужно:
1. Установите пакетный менеджер и утилиту для создания виртуального окружения.
   ```
   sudo apt install python3-pip python3-venv -y
   ```

2. В директории с проектом и создайте виртуальное окружение и активируйте его.
   ```
   python3 -m venv venv
   source venv/bin/activate
   ```
   
3. Установите зависимости проекта.
   ```
   pip install -r requirements.txt
   ```

4. Выполните миграции для базы данных.
   ```
   python manage.py migrate
   ```

5. Создайте суперпользователя для проекта.
   ```
   python manage.py createsuperuser
   ```

6. Отредактируйте файл settings.py на сервере. Добавьте в список ALLOWED_HOSTS внешний IP-адрес вашего сервера, а также адреса 127.0.0.1 и localhost. Пример:
   ```
   ALLOWED_HOSTS = ['<внешний адрес вашего сервера>', '127.0.0.1', 'localhost']

## Запуск frontend проекта на сервере

1. Установите Node.js на сервере с помощью команд: 
   ```
   curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
   sudo apt-get install -y nodejs
   ```

2. Установите зависимости frontend приложения. В директории `<ваш проект>/frontend/` выполните команду `npm i`.

Установка и запуск Gunicorn

Чтобы установить и запустить Gunicorn, следуйте приведенным ниже шагам:

1. Активируйте виртуальное окружение вашего проекта. Если у вас его еще нет, создайте виртуальное окружение с помощью инструмента, такого как virtualenv или venv.

2. Установите пакет Gunicorn, выполнив следующую команду:

   ```
   pip install gunicorn==20.1.0
   ```

   Это установит последнюю стабильную версию Gunicorn.

3. Откройте файл settings.py в корневой папке вашего проекта и установите значение False для константы DEBUG:

   ```
   DEBUG = False
   ```

   Это поможет вам переключить проект в режим без отладки.

4. Создайте файл gunicorn.service в директории /etc/systemd/system/ с помощью текстового редактора командной строки, такого как nano или vim:

   ```
   sudo nano /etc/systemd/system/gunicorn.service
   ```

5. Вставьте следующий код в файл gunicorn.service:

   ```
   [Unit]
   Description=Gunicorn service
   After=network.target

   [Service]
   User=your_username
   Group=your_group
   WorkingDirectory=/path/to/your/project
   ExecStart=/path/to/your/virtualenv/bin/gunicorn --access-logfile - --workers 3 --bind unix:/path/to/your/project/project.sock project.wsgi:application

   [Install]
   WantedBy=multi-user.target
   ```

   Замените `your_username` на ваше имя пользователя, `your_group` на вашу группу пользователей, `/path/to/your/project` на путь к корневой папке вашего проекта, и `/path/to/your/virtualenv` на путь к вашему виртуальному окружению. Убедитесь, что вы указали правильный путь к файлу wsgi.py в вашем проекте.

6. Сохраните и закройте файл.

Теперь у вас должен быть настроен и готов к использованию сервис Gunicorn. Вы можете запустить его, выполнив следующую команду:

```
sudo systemctl start gunicorn
```

Чтобы Gunicorn запускался автоматически при загрузке системы, выполните следующую команду:

```
sudo systemctl enable gunicorn
```
## Установка и настройка Nginx

1. Установите Nginx на вашем сервере, выполните следующую команду из любой директории:
   ```sudo apt install nginx -y```

2. Для установки ограничений на открытые порты выполните по очереди следующие команды:
   ```
   sudo ufw allow 'Nginx Full'
   sudo ufw allow OpenSSH
   ```

3. Включите файервол:
   ```
   sudo ufw enable
   ```

4. Соберите и разместите статику для frontend-приложения.
   - Перейдите в директорию `<имя_проекта>/frontend/`.
   - Выполните команду `npm run build`. Результат будет сохранен в директории `<имя_проекта>/frontend/build/`.
   - Скопируйте содержимое папки `/frontend/build/` в системную директорию сервера `/var/www/`.

5. Откройте файл конфигурации веб-сервера:
   ```
   sudo nano /etc/nginx/sites-enabled/default
   ```

6. Замените его содержимое следующим кодом:
   ```
   server {
       listen 80;
       server_name публичный_ip_вашего_удаленного_сервера;
   
       location / {
           root   /var/www/<имя_проекта>;
           index  index.html index.htm;
           try_files $uri /index.html;
       }
   }
   ```

7. Проверьте корректность конфигурации:
   ```
   sudo nginx -t
   ```

8. Перезагрузите конфигурацию Nginx:
   ```
   sudo systemctl reload nginx
   ```

9. Настройте проксирование запросов.

10. Откройте файл конфигурации Nginx:
    ```
    sudo nano /etc/nginx/sites-enabled/default
    ```

11. Добавьте следующий блок location:
    ```
    server {
        listen 80;
        server_name публичный_ip_вашего_удаленного_сервера;
    
        location /api/ {
            proxy_pass http://127.0.0.1:8080;
        }
        
        location /admin/ {
            proxy_pass http://127.0.0.1:8000;
        }
      
        location / {
            root   /var/www/<имя_проекта>;
            index  index.html index.htm;
            try_files $uri /index.html;
        }
    }
    ```

12. Сохраните изменения, проверьте и перезагрузите конфигурацию веб-сервера:
    ```
    sudo nginx -t
    sudo systemctl reload nginx
    ```

13. Соберите и настройте статику для backend-приложения.

14. В файле `settings.py` вашего проекта пропишите следующие настройки:
    ```
    STATIC_URL = 'static_backend'
    STATIC_ROOT = BASE_DIR / 'static_backend'
    ```

15. Активируйте виртуальное окружение проекта, перейдите в директорию с файлом `manage.py` и выполните команду:
    ```
    python manage.py collectstatic
    ```

16. В директории `<имя_проекта>/backend/` будет создана директория `static_backend/`.

17. Скопируйте директорию `static_backend/` в директорию `/var/www/<имя_проекта>/`.

## Добавление доменного имени в настройки Django

1. Находясь на сервере, перейдите в директорию /taski/backend/backend, с помощью Nano откройте файл settings.py и добавьте в список ALLOWED_HOSTS полученное доменное имя:
```
ALLOWED_HOSTS = ['xxx.xxx.xxx.xxx', '127.0.0.1', 'localhost', 'ваш-домен'] 
# Вместо xxx.xxx.xxx.xxx — IP вашего сервера.
# Домен вводится в формате 'project.hopto.org'. 
```

2. Измените конфигурационный файл Nginx.

```
server {
...
    server_name <ваш-ip> <ваш-домен>;
...
} 
```

3. После этого проверьте конфигурацию `sudo nginx -t` и перезагрузите её командой `sudo systemctl reload nginx`, чтобы изменения вступили в силу.
