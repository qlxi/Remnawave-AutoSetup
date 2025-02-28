<div align="center">
  <h1 style="color: #00bcd4;">Remnawave Auto-Installer</h1>
  <p>Профессиональный скрипт для автоматической установки панели Remnawave и подключения узлов на Linux</p>
  <img src="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/52637e61cc545ce5b096ea3359758b4629451c96/remnawave_screenshot.png?raw=true" alt="Скриншот Remnawave" style="width: 80%; max-width: 800px; margin: 20px 0;">
  
  <!-- Значки лицензии, версии и платформы -->
  <div style="display: flex; justify-content: center; gap: 15px; margin-top: 20px;">
    <img src="https://img.shields.io/badge/Platform-Linux-brightgreen" alt="Linux">
    <img src="https://img.shields.io/badge/Version-v0.1%20(Beta)-orange" alt="Версия">
    <img src="https://img.shields.io/badge/License-MIT-blue" alt="Лицензия MIT">
  </div>

  <br><br>
  <div style="font-size: 14px;">
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/README.md" style="text-decoration: none; color: #007bff;">English</a> | 
    <a href="[#](https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-fa.md)" style="text-decoration: none; color: #007bff;">فارسی</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-ru.md" style="text-decoration: none; color: #007bff;">Русский</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-zh.md/" style="text-decoration: none; color: #007bff;">中文</a>
  </div>
</div>

## Требования

- Ubuntu 20.04 или выше
- Минимум 1 ГБ оперативной памяти
- 10 ГБ свободного места на диске
- Root доступ к серверу
- Действующее доменное имя (для SSL)
- Домен должен быть направлен на IP-адрес вашего сервера

## Возможности

- **Безопасность**
  - Продвинутое шифрование: Современные протоколы шифрования для максимальной безопасности
  - Система защиты от атак: Встроенная защита от DDoS и других кибератак
  - Скрытие IP: Продвинутые функции маскировки и защиты IP
  - Многоуровневая защита: Несколько уровней безопасности для защиты ваших данных

- **Производительность**
  - Высокая скорость работы: Оптимизировано для максимальной скорости и минимальной задержки
  - Балансировка нагрузки: Умное распределение трафика между узлами
  - Неограниченная пропускная способность: Без ограничений на передачу данных
  - Глобальная сеть: Доступ к серверам по всему миру

- **Управление**
  - Простое управление панелью: Удобный интерфейс для легкого администрирования
  - Мониторинг в реальном времени: Отслеживание всех подключений и трафика
  - Автоматическая настройка: Автоматическая установка и конфигурация
  - Многопользовательская система: Поддержка нескольких учетных записей и прав доступа

- **Технические характеристики**
  - Интеграция с Docker: Полная поддержка контейнеризации
  - Интеграция с Nginx: Расширенная настройка веб-сервера
  - SSL-сертификат: Автоматическая настройка и обновление SSL-сертификатов
  - Управление узлами: Простое добавление и настройка новых узлов
  - Интеграция с Telegram: Встроенный бот для уведомлений и управления

- **Аналитика и отчетность**
  - Анализ трафика: Детальный мониторинг и анализ трафика
  - Статистика использования: Комплексная статистика и отчеты
  - Отслеживание пользователей: Мониторинг активности пользователей
  - Системные логи: Подробные системные журналы для устранения неполадок

- **Дополнительные функции**
  - Многоязычная поддержка: Интерфейс доступен на нескольких языках
  - Регулярные обновления: Постоянные обновления и улучшения системы
  - Время работы 24/7: Разработано для непрерывной работы
  - Система резервного копирования: Автоматическое резервное копирование и восстановление

> **Примечание**: Требуется Ubuntu 20.04 или выше.

---

### Автоматическая установка

Выполните следующую команду в терминале для автоматической установки Remnawave:

```sh
wget -O start.sh https://raw.githubusercontent.com/AsanFillter/Remnawave-AutoSetup/main/start.sh && chmod +x start.sh && ./start.sh
```

<details>
<summary><b>Ручная установка</b></summary>

### Этапы установки панели

1. Установка необходимых компонентов:
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

3. Добавьте следующее содержимое в `jwtgen.py`:
```python
import secrets

# Generate JWT_AUTH_SECRET
jwt_auth_secret = secrets.token_hex(32)
print("JWT_AUTH_SECRET:", jwt_auth_secret)

# Generate JWT_API_TOKENS_SECRET
jwt_api_tokens_secret = secrets.token_hex(32)
print("JWT_API_TOKENS_SECRET:", jwt_api_tokens_secret)
```

4. Запустите скрипт для генерации JWT секретов:
```sh
python3 jwtgen.py
```

5. Сохраните сгенерированные HEX-коды для дальнейшего использования.

6. Создайте директорию для Remnawave и перейдите в неё:
```sh
mkdir remnawave && cd remnawave
```

7. Загрузите конфигурационный файл проекта:
```sh
curl -o .env https://raw.githubusercontent.com/remnawave/backend/refs/heads/main/.env.sample
```

8. Отредактируйте конфигурационный файл:
```sh
nano .env
```

9. Замените заполнители правильными значениями:
```env
### APP ###
APP_PORT=3000

DATABASE_URL="postgresql://postgres:postgres@remnawave-db:5432/postgres"

### JWT ###
### ИЗМЕНИТЕ ЗНАЧЕНИЯ ПО УМОЛЧАНИЮ ###
JWT_AUTH_SECRET=ВашПервыйHexКод
JWT_API_TOKENS_SECRET=ВашВторойHexКод

### TELEGRAM ###
TELEGRAM_BOT_TOKEN=ТокенВашегоТелеграмБота
TELEGRAM_ADMIN_ID=ВашТелеграмАдминID
NODES_NOTIFY_CHAT_ID=ВашТелеграмЧатID

### FRONT_END ###
FRONT_END_DOMAIN=*

### SUBSCRIPTION ###
SUB_SUPPORT_URL=https://ВашПоддомен
SUB_PROFILE_TITLE=Профиль подписки
SUB_UPDATE_INTERVAL=12
SUB_WEBPAGE_URL=https://ВашПоддомен

### SUBSCRIPTION PUBLIC DOMAIN ###
### RAW DOMAIN, БЕЗ HTTP/HTTPS, НЕ СТАВЬТЕ / в конце домена ###
SUB_PUBLIC_DOMAIN=rw.guilanit.com

EXPIRED_USER_REMARKS=["Подписка истекла","Свяжитесь с поддержкой"]
DISABLED_USER_REMARKS=["Подписка отключена","Свяжитесь с поддержкой"]
LIMITED_USER_REMARKS=["Подписка ограничена","Свяжитесь с поддержкой"]

### SUPERADMIN ###
### ИЗМЕНИТЕ ЗНАЧЕНИЯ ПО УМОЛЧАНИЮ ###
SUPERADMIN_USERNAME=ВашеИмяАдмина
SUPERADMIN_PASSWORD=ВашПарольАдмина

### SWAGGER ###
SWAGGER_PATH=/docs
SCALAR_PATH=/scalar
IS_DOCS_ENABLED=true

### PROMETHEUS ###
METRICS_USER=admin
METRICS_PASS=admin

### WEBHOOK ###
WEBHOOK_ENABLED=true
### Разрешен только https:// ###
WEBHOOK_URL=https://webhook.site/1234567890
### Этот секрет используется для подписи webhook payload, должен быть ровно 64 символа. Разрешены только a-z, 0-9, A-Z ###
WEBHOOK_SECRET_HEADER=vsmu67Kmg6R8FjIOF1WUY8LWBHie4scdEqrfsKmyf4IAf8dY3nFS0wwYHkhh6ZvQ

### CLOUDFLARE ###
# ИСПОЛЬЗУЕТСЯ ТОЛЬКО ДЛЯ docker-compose-prod-with-cf.yml
# НЕ ИСПОЛЬЗУЕТСЯ САМИМ ПРИЛОЖЕНИЕМ
CLOUDFLARE_TOKEN=ey...

### Database ###
### Для контейнера Postgres Docker ###
# НЕ ИСПОЛЬЗУЕТСЯ САМИМ ПРИЛОЖЕНИЕМ
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=postgres
```

10. Создайте файл Docker Compose:
```sh
nano docker-compose.yml
```

11. Добавьте следующее содержимое в `docker-compose.yml`:
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

12. Выполните следующую команду для запуска контейнеров:
```sh
docker compose up -d
```

13. Проверьте логи, чтобы убедиться, что всё работает правильно:
```sh
docker compose logs -f
```

### Инструкции по настройке узла

После установки основной панели создайте новый виртуальный сервер с желаемым расположением.

1. Сначала установите Docker на ваш сервер:
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

3. Создайте директорию для узла и создайте файл Docker:
```sh
mkdir /remnanode && cd /remnanode && nano docker-compose.yml
```

4. Добавьте следующее содержимое в `docker-compose.yml`:
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

6. Перейдите в вашу панель и добавьте узел. Нажмите на "Важная информация" и скопируйте ключ. Добавьте его в ваш файл .env:
```env
### APP ###
APP_PORT=2222
```

7. Запустите контейнер Docker и проверьте логи:
```sh
docker compose up -d && docker compose logs -f
```

</details>

## Вклад в проект

Мы всегда рады вашему участию! Вот как вы можете помочь:

- Сообщать об ошибках или проблемах
- Предлагать новые функции
- Улучшать документацию
- Проверять изменения в коде

## Поддержка

[![Смотреть обучающее видео](https://github.com/AsanFillter/Remnawave-AutoSetup/raw/main/img/thumbnail.jpg)](https://www.youtube.com/watch?v=AM2ppG1kTFI)

Если вы считаете этот проект полезным, пожалуйста, поставьте ему звезду на GitHub!

- **Telegram канал:** [@AsanFillter](https://t.me/AsanFillter)  
- **Telegram группа:** [@AsanFillter_Group](https://t.me/asanfillter_group)

Для получения дополнительной информации и документации, пожалуйста, посетите [официальный сайт Remnawave](https://remna.st/).
