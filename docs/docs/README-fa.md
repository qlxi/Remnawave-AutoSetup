<div align="center">
  <h1 style="color: #00bcd4;">نصب کننده خودکار Remnawave</h1>
  <p>اسکریپت حرفه‌ ای برای نصب خودکار پنل Remnawave و اتصال نود در لینوکس</p>
  <img src="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/52637e61cc545ce5b096ea3359758b4629451c96/remnawave_screenshot.png?raw=true" alt="تصویر Remnawave" style="width: 80%; max-width: 800px; margin: 20px 0;">
  
  <!-- نشان‌های لایسنس، نسخه و پلتفرم -->
  <div style="display: flex; justify-content: center; gap: 15px; margin-top: 20px;">
    <img src="https://img.shields.io/badge/Platform-Linux-brightgreen" alt="لینوکس">
    <img src="https://img.shields.io/badge/Version-v0.1%20(Beta)-orange" alt="نسخه">
    <img src="https://img.shields.io/badge/License-MIT-blue" alt="لایسنس MIT">
  </div>

  <br><br>
  <div style="font-size: 14px;">
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/README.md" style="text-decoration: none; color: #007bff;">English</a> | 
    <a href="#" style="text-decoration: none; color: #007bff;">فارسی</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/docs/README-ru.md" style="text-decoration: none; color: #007bff;">Русский</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/docs/README-zh.md" style="text-decoration: none; color: #007bff;">中文</a>
  </div>
</div>

## پیش‌نیازها

- اوبونتو ۲۰.۰۴ یا بالاتر
- حداقل ۱ گیگابایت رم
- ۱۰ گیگابایت فضای خالی دیسک
- دسترسی روت به سرور
- دامنه معتبر (برای SSL)
- تنظیم DNS دامنه به آی‌پی سرور

## ویژگی‌ها

- **امنیت**
  - رمزنگاری پیشرفته: پروتکل‌های رمزنگاری پیشرفته برای حداکثر امنیت
  - سیستم ضد حمله: محافظت داخلی در برابر حملات DDoS و سایر حملات سایبری
  - مخفی‌سازی IP: ویژگی‌های پیشرفته مخفی‌سازی و محافظت از IP
  - امنیت چندلایه: چندین لایه امنیتی برای محافظت از داده‌های شما

- **کارایی**
  - عملکرد با سرعت بالا: بهینه‌سازی شده برای حداکثر سرعت و حداقل تأخیر
  - تعادل بار: توزیع هوشمند ترافیک بین چندین نود
  - پهنای باند نامحدود: بدون محدودیت در انتقال داده
  - شبکه جهانی: دسترسی به سرورها در سراسر جهان

- **مدیریت**
  - مدیریت آسان پنل: رابط کاربری ساده برای مدیریت آسان
  - نظارت بلادرنگ: نظارت زنده بر تمام اتصالات و ترافیک
  - پیکربندی خودکار: راه‌اندازی و پیکربندی اتوماتیک
  - سیستم چند کاربره: پشتیبانی از چندین حساب کاربری و سطوح دسترسی

- **ویژگی‌های فنی**
  - ادغام با داکر: پشتیبانی کامل از کانتینرسازی با داکر
  - ادغام با Nginx: پیکربندی پیشرفته وب سرور با Nginx
  - گواهی SSL: راه‌اندازی و تمدید خودکار گواهی SSL
  - مدیریت نود: افزودن و پیکربندی آسان نودهای جدید
  - ادغام با تلگرام: ربات تلگرام داخلی برای اطلاع‌رسانی و کنترل

- **تجزیه و تحلیل و گزارش‌گیری**
  - تحلیل ترافیک: نظارت و تحلیل دقیق ترافیک
  - آمار استفاده: آمار و گزارش‌های جامع استفاده
  - ردیابی کاربر: نظارت بر فعالیت‌ها و اتصالات کاربران
  - لاگ‌های سیستم: لاگ‌های دقیق سیستم برای عیب‌یابی

- **ویژگی‌های اضافی**
  - پشتیبانی چند زبانه: رابط کاربری در زبان‌های مختلف
  - به‌روزرسانی‌های منظم: به‌روزرسانی و بهبود مداوم سیستم
  - دسترسی ۲۴/۷: طراحی شده برای کارکرد مداوم
  - سیستم پشتیبان‌گیری: قابلیت پشتیبان‌گیری و بازیابی خودکار

> **نکته**: نیاز به اوبونتو ۲۰.۰۴ یا بالاتر دارد.

---

### نصب خودکار

دستور زیر را در ترمینال خود اجرا کنید تا Remnawave به صورت خودکار نصب شود:

```sh
curl -s https://raw.githubusercontent.com/AsanFillter/Remnawave-AutoSetup/dfe140d1cb758bbc9f7f4485977b4d65ff5833f9/install_remnawave.sh | bash
```

<details>
<summary><b>نصب دستی</b></summary>

### مراحل نصب پنل

1. نصب پیش‌نیازها:
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. ایجاد فایل جدید با نام `jwtgen.py`:
```sh
nano jwtgen.py
```

3. افزودن محتوای زیر به `jwtgen.py`:
```python
import secrets

# Generate JWT_AUTH_SECRET
jwt_auth_secret = secrets.token_hex(32)
print("JWT_AUTH_SECRET:", jwt_auth_secret)

# Generate JWT_API_TOKENS_SECRET
jwt_api_tokens_secret = secrets.token_hex(32)
print("JWT_API_TOKENS_SECRET:", jwt_api_tokens_secret)
```

4. اجرای اسکریپت برای تولید کلیدهای JWT:
```sh
python3 jwtgen.py
```

5. کدهای HEX تولید شده را برای استفاده بعدی ذخیره کنید.

6. ایجاد پوشه برای Remnawave و ورود به آن:
```sh
mkdir remnawave && cd remnawave
```

7. دانلود فایل پیکربندی پروژه:
```sh
curl -o .env https://raw.githubusercontent.com/remnawave/backend/refs/heads/main/.env.sample
```

8. ویرایش فایل پیکربندی:
```sh
nano .env
```

9. جایگزین کردن مقادیر با مقادیر صحیح:
```env
### APP ###
APP_PORT=3000

DATABASE_URL="postgresql://postgres:postgres@remnawave-db:5432/postgres"

### JWT ###
### CHANGE DEFAULT VALUES ###
JWT_AUTH_SECRET=کد_هگز_اول_شما
JWT_API_TOKENS_SECRET=کد_هگز_دوم_شما

### TELEGRAM ###
TELEGRAM_BOT_TOKEN=توکن_ربات_تلگرام_شما
TELEGRAM_ADMIN_ID=آیدی_ادمین_تلگرام_شما
NODES_NOTIFY_CHAT_ID=آیدی_چت_تلگرام_شما

### FRONT_END ###
FRONT_END_DOMAIN=*

### SUBSCRIPTION ###
SUB_SUPPORT_URL=https://ساب‌دامنه_شما
SUB_PROFILE_TITLE=پروفایل اشتراک
SUB_UPDATE_INTERVAL=12
SUB_WEBPAGE_URL=https://ساب‌دامنه_شما

### SUBSCRIPTION PUBLIC DOMAIN ###
### RAW DOMAIN, WITHOUT HTTP/HTTPS, DO NOT PLACE / to end of domain ###
SUB_PUBLIC_DOMAIN=rw.guilanit.com

EXPIRED_USER_REMARKS=["اشتراک منقضی شده","با پشتیبانی تماس بگیرید"]
DISABLED_USER_REMARKS=["اشتراک غیرفعال شده","با پشتیبانی تماس بگیرید"]
LIMITED_USER_REMARKS=["اشتراک محدود شده","با پشتیبانی تماس بگیرید"]

### SUPERADMIN ###
### CHANGE DEFAULT VALUES ###
SUPERADMIN_USERNAME=نام_کاربری_ادمین_شما
SUPERADMIN_PASSWORD=رمز_عبور_ادمین_شما

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

10. ایجاد فایل Docker Compose:
```sh
nano docker-compose.yml
```

11. افزودن محتوای زیر به `docker-compose.yml`:
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

12. اجرای دستور زیر برای راه‌اندازی کانتینرها:
```sh
docker compose up -d
```

13. بررسی لاگ‌ها برای اطمینان از صحت اجرا:
```sh
docker compose logs -f
```

### دستورالعمل راه‌اندازی نود

پس از نصب پنل اصلی، یک سرور مجازی جدید با موقعیت مکانی دلخواه خود ایجاد کنید.

1. ابتدا داکر را روی سرور نصب کنید:
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. سرور خود را به‌روزرسانی کنید:
```sh
sudo apt update && apt upgrade -y
```

3. یک پوشه برای نود ایجاد کرده و فایل داکر را بسازید:
```sh
mkdir /remnanode && cd /remnanode && nano docker-compose.yml
```

4. محتوای زیر را به `docker-compose.yml` اضافه کنید:
```yaml
services:
  remnanode:
    container_name: remnanode
    hostname: remnanode
    image:
