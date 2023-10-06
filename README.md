# Docker-notes

Проект таск-трекера для практики развертывания на сервере и настройки CI&CD. Репозиторий содержит код Docker-контейнеров для развертывания приложения на сервере. 

## Использование

- Скопируйте репозиторий на свой локальный компьютер:

```
git clone https://github.com/atsterq/Docker-notes
```

- Локально отредактируйте файл infra/nginx.conf и в строке server_name впишите свой IP

- Подключитесь к вашему серверу с помощью SSH:
```
ssh <server user>@<server IP>
```

- Установите Docker на вашем сервере:
```
sudo apt install docker.io
```

- Установите Docker Compose (для Linux):
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

- Получите разрешения для docker-compose:
```
sudo chmod +x /usr/local/bin/docker-compose
```

- Создайте директорию проекта (желательно в вашей домашней директории):
```
mkdir Docker-notes && cd Docker-notes/
```

- Скопируйте файлы из 'infra/' (на вашем локальном компьютере) на ваш сервер:
```
scp -r infra/* <server user>@<server IP>:/home/<server user>/Docker-notes/
```

- Cоздайте .env файл:
```
mv .env.example .env
```

- И впишите в него:
```
POSTGRES_DB=<имя базы данных postgres>
POSTGRES_USER=<пользователь бд>
POSTGRES_PASSWORD=<пароль>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=секретный ключ проекта django>
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,158.160.70.1,0.0.0.0,<IP или название вашего сервера>
```

- Запустите docker-compose:
```
sudo docker-compose.production up -d
```

## Структура проекта

- `docker-compose.production.yml` - файл конфигурации Docker Compose.
- `Dockerfile` - файл для создания образа Docker.
- `requirements.txt` - файл с зависимостями Python.
- `backend/` - директория с исходным кодом бэкенда приложения.
- `frontend/` - директория с исходным кодом фронтенда приложения.
- `gateway/` - директория с файлом конфигурации nginx.

## Поддержка

Если у вас возникли проблемы с использованием проекта, пожалуйста, создайте issue в репозитории. 

## Лицензия

Этот проект лицензирован по лицензии MIT. Подробности смотрите в файле `LICENSE`.
