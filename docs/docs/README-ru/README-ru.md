<div align="center">
  <h1 style="color: #00bcd4;">Авто-установщик Remnawave</h1>
  <p>Профессиональный скрипт для автоматической установки панели Remnawave и подключения узлов на Linux</p>
  <img src="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/52637e61cc545ce5b096ea3359758b4629451c96/remnawave_screenshot.png?raw=true" alt="Скриншот Remnawave" style="width: 80%; max-width: 800px; margin: 20px 0;">
  
  <!-- Лицензия, Версия и Платформа значки -->
  <div style="display: flex; justify-content: center; gap: 15px; margin-top: 20px;">
    <img src="https://img.shields.io/badge/Platform-Linux-brightgreen" alt="Linux">
    <img src="https://img.shields.io/badge/Version-v0.1%20(Beta)-orange" alt="Version">
    <img src="https://img.shields.io/badge/License-MIT-blue" alt="MIT License">
  </div>

  <br><br>
  <div style="font-size: 14px;">
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/README.md" style="text-decoration: none; color: #007bff;">English</a> | 
    <a href="#" style="text-decoration: none; color: #007bff;">فارسی</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/docs/README-ru.md" style="text-decoration: none; color: #007bff;">Русский</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/docs/README-zh.md" style="text-decoration: none; color: #007bff;">中文</a>
  </div>
</div>

## Требования

- Ubuntu 20.04 или выше
- Минимум 1GB оперативной памяти
- 10GB свободного места на диске
- Доступ к серверу с правами root
- Действующее доменное имя (для SSL)
- Домен, указывающий на IP вашего сервера

## Возможности

- **Безопасность**
  - Продвинутое шифрование: Современные протоколы шифрования для максимальной безопасности
  - Система защиты от атак: Встроенная защита от DDoS и других кибер-атак
  - Сокрытие IP: Продвинутые функции маскировки и защиты IP
  - Многоуровневая безопасность: Несколько уровней защиты данных

- **Производительность**
  - Высокая скорость: Оптимизация для максимальной скорости и минимальной задержки
  - Балансировка нагрузки: Умное распределение трафика между несколькими узлами
  - Неограниченная пропускная способность: Без ограничений на передачу данных
  - Глобальная сеть: Доступ к серверам по всему миру

- **Управление**
  - Простое управление панелью: Удобный интерфейс для легкого администрирования
  - Мониторинг в реальном времени: Живой мониторинг всех подключений и трафика
  - Автоматическая конфигурация: Автоматическая настройка и конфигурация
  - Многопользовательская система: Поддержка нескольких учетных записей и разрешений

- **Технические возможности**
  - Интеграция с Docker: Поддержка полной контейнеризации с Docker
  - Интеграция с Nginx: Продвинутая настройка веб-сервера с Nginx
  - Сертификат SSL: Автоматическая настройка и обновление SSL-сертификатов
  - Управление узлами: Легкое добавление и настройка новых узлов
  - Интеграция с Telegram: Встроенный бот Telegram для уведомлений и управления

- **Аналитика и отчеты**
  - Аналитика трафика: Детальный мониторинг и анализ трафика
  - Статистика использования: Комплексные отчеты и статистика использования
  - Отслеживание пользователей: Мониторинг активности пользователей и подключений
  - Системные логи: Детализированные системные логи для устранения неполадок

- **Дополнительные функции**
  - Поддержка нескольких языков: Интерфейс доступен на нескольких языках
  - Регулярные обновления: Постоянные обновления и улучшения системы
  - 24/7 доступность: Разработано для непрерывной работы
  - Система резервного копирования: Автоматическое резервное копирование и восстановление

> **Примечание**: Требуется Ubuntu 20.04 или выше.

---

### Автоматическая установка

Выполните следующую команду в вашем терминале для автоматической установки Remnawave:

```sh
curl -s https://raw.githubusercontent.com/AsanFillter/Remnawave-AutoSetup/dfe140d1cb758bbc9f7f4485977b4d65ff5833f9/install_remnawave.sh | bash
```

<details>
<summary><b>Ручная установка</b></summary>

### Шаги установки панели

1. Установите необходимые компоненты:
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. Создайте новый файл с именем `jwtgen.py`:
```sh
nano jwtgen.py
```

3. Добавьте следующий контент в `jwtgen.py`:
```python
import secrets

# Генерация JWT_AUTH_SECRET
jwt_auth_secret = secrets.token_hex(32)
print("JWT_AUTH_SECRET:", jwt_auth_secret)

# Генерация JWT_API_TOKENS_SECRET
jwt_api_tokens_secret = secrets.token_hex(32)
print("JWT_API_TOKENS_SECRET:", jwt_api_tokens_secret)
```

4. Запустите скрипт для генерации секретов JWT:
```sh
python3 jwtgen.py
```

5. Сохраните сгенерированные HEX-коды для дальнейшего использования.

6. Создайте директорию для Remnawave и перейдите в нее:
```sh
mkdir remnawave && cd remnawave
```

7. Скачайте файл конфигурации проекта:
```sh
curl -o .env https://raw.githubusercontent.com/remnawave/backend/refs/heads/main/.env.sample
```

8. Отредактируйте файл конфигурации:
```sh
nano .env
```

9. Замените заполнители правильными значениями:
```env
### APP ###
APP_PORT=3000

DATABASE_URL="postgresql://postgres:postgres@remnawave-db:5432/postgres"

### JWT ###
### CHANGE DEFAULT VALUES ###
JWT_AUTH_SECRET=YourFirstHexCode
JWT_API_TOKENS_SECRET=YourSecondHexCode

### TELEGRAM ###
TELEGRAM_BOT_TOKEN=YourTelegramBotToken
TELEGRAM_ADMIN_ID=YourTelegramAdminID
NODES_NOTIFY_CHAT_ID=YourTelegramChatID

### FRONT_END ###
FRONT_END_DOMAIN=*

### SUBSCRIPTION ###
SUB_SUPPORT_URL=https://YourSubdomain
SUB_PROFILE_TITLE=Subscription Profile
SUB_UPDATE_INTERVAL=12
SUB_WEBPAGE_URL=https://YourSubdomain

### SUBSCRIPTION PUBLIC DOMAIN ###
### RAW DOMAIN, WITHOUT HTTP/HTTPS, DO NOT PLACE / to end of domain ###
SUB_PUBLIC_DOMAIN=rw.guilanit.com

EXPIRED_USER_REMARKS=["Subscription expired","Contact support"]
DISABLED_USER_REMARKS=["Subscription disabled","Contact support"]
LIMITED_USER_REMARKS=["Subscription limited","Contact support"]

### SUPERADMIN ###
### CHANGE DEFAULT VALUES ###
SUPERADMIN_USERNAME=YourAdminUsername
SUPERADMIN_PASSWORD=YourAdminPassword

### SWAGGER ###
SWAGGER_PATH=/docs
SCALAR_PATH=/scalar
IS_DOCS_ENABLED=true

### PROMETHEUS ###
METRICS_USER=admin
METRICS_PASS=admin

### WEBHOOK ###
WEBHOOK_ENABLED=true
### Only https:// is allowed
WEBHOOK_URL=https://webhook.site/1234567890
### This secret is used to sign the webhook payload, must be exact 64 characters. Only a-z, 0-9, A-Z are allowed.
WEBHOOK_SECRET_HEADER=vsmu67Kmg6R8FjIOF1WUY8LWBHie4scdEqrfsKmyf4IAf8dY3nFS0wwYHkhh6ZvQ

### CLOUDFLARE ###
# USED ONLY FOR docker-compose-prod-with-cf.yml
# NOT USED BY THE APP ITSELF
CLOUDFLARE_TOKEN=ey...

### Database ###
### For Postgres Docker container ###
# NOT USED BY THE APP ITSELF
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=postgres
```

10. Создайте файл Docker Compose:
```sh
nano docker-compose.yml
```

11. Добавьте следующий контент в `docker-compose.yml`:
```yaml
services:
    remnawave-db:
        image: postgres:17
        container_name: 'remnawave-db'
        hostname: remnawave-db
        restart: always
        env_file:
            - .env
        environment:
            - POSTGRES_USER=${POSTGRES_USER}
            - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
            - POSTGRES_DB=${POSTGRES_DB}
            - TZ=UTC
        ports:
            - '127.0.0.1:6767:5432'
        volumes:
            - remnawave-db-data:/var/lib/postgresql/data
        networks:
            - remnawave-network
        healthcheck:
            test: ['CMD-SHELL', 'pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}']
            interval: 3s
            timeout: 10s
            retries: 3

    remnawave:
        image: remnawave/backend:latest
        container_name: 'remnawave'
        hostname: remnawave
        restart: always
        ports:
            - '127.0.0.1:3000:3000'
        env_file:
            - .env
        networks:
            - remnawave-network

networks:
    remnawave-network:
        name: remnawave-network
        driver: bridge
        external: false

volumes:
    remnawave-db-data:
        driver: local
        external: false
        name: remnawave-db-data
```

12. Запустите следующую команду для старта контейнеров:
```sh
docker compose up -d
```

13. Проверьте логи, чтобы убедиться, что все работает корректно:
```sh
docker compose logs -f
```

### Инструкции по настройке узла

После установки основной панели создайте новый виртуальный сервер в нужном вам месте.

1. Сначала установите Docker на сервер:
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. Обновите ваш сервер:
```sh
sudo apt update && apt upgrade -y
```

3. Создайте директорию для узла и создайте Docker файл:
```sh
mkdir /remnanode && cd /remnanode && nano docker-compose.yml
```

4. Добавьте следующий контент в `docker-compose.yml`:
```yaml
services:
  remnanode:
    container_name: remnanode
    hostname: remnanode
    image: remnawave/node:latest
    env_file:
      - .env
    network_mode: host
```

5. Создайте и отредактируйте файл .env:
```sh
nano .env
```

6. Перейдите на вашу панель и добавьте узел. Нажмите на "Важная информация" и скопируйте ключ. Добавьте его в ваш .env файл:
```env
### APP ###
APP_PORT=2222
```

7. Запустите Docker контейнер и проверьте логи:
```sh
docker compose up -d && docker compose logs -f
```

</details>

## Вклад

Вклад всегда приветствуется! Вот как вы можете помочь:

- Сообщить об ошибках или проблемах
- Предложить новые функции
- Улучшить документацию
- Проверить изменения кода

## Поддержка

Если вы считаете этот проект полезным, пожалуйста, поставьте звезду на GitHub!

- **Канал Telegram:** [@AsanFillter](https://t.me/AsanFillter)  
- **Группа Telegram:** [@AsanFillter_Group](https://t.me/asanfillter_group)

Для получения дополнительной информации и документации посетите [официальный сайт Remnawave](https://remnawave.com).
