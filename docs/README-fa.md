<div dir="rtl" align="center">
  <h1 style="color: #00bcd4;">نصب خودکار Remnawave</h1>
  <p>اسکریپت حرفه‌ای برای نصب خودکار پنل Remnawave و اتصال نود در لینوکس</p>
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
    <a href="[#](https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-fa.md)" style="text-decoration: none; color: #007bff;">فارسی</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-ru.md" style="text-decoration: none; color: #007bff;">Русский</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-zh.md/" style="text-decoration: none; color: #007bff;">中文</a>
  </div>
</div>

## پیش‌نیازها

- اوبونتو ۲۰.۰۴ یا بالاتر
- حداقل ۱ گیگابایت رم
- ۱۰ گیگابایت فضای خالی دیسک
- دسترسی روت به سرور
- دامنه معتبر (برای SSL)
- تنظیم DNS دامنه به IP سرور شما

## ویژگی‌ها

- **امنیت**
  - رمزنگاری پیشرفته: پروتکل‌های رمزنگاری پیشرفته برای حداکثر امنیت
  - سیستم ضد حمله: محافظت داخلی در برابر حملات DDoS و سایر حملات سایبری
  - مخفی‌سازی IP: ویژگی‌های پیشرفته محافظت و مخفی‌سازی IP
  - امنیت چندلایه: لایه‌های متعدد امنیتی برای محافظت از داده‌های شما

- **کارایی**
  - عملکرد سرعت بالا: بهینه‌سازی شده برای حداکثر سرعت و حداقل تأخیر
  - متعادل‌کننده بار: توزیع هوشمند ترافیک بین چندین نود
  - پهنای باند نامحدود: بدون محدودیت در انتقال داده
  - شبکه جهانی: دسترسی به سرورها در سراسر جهان

- **مدیریت**
  - مدیریت آسان پنل: رابط کاربری آسان برای مدیریت
  - نظارت بلادرنگ: نظارت زنده بر تمام اتصالات و ترافیک
  - پیکربندی خودکار: راه‌اندازی و پیکربندی اتوماتیک
  - سیستم چند کاربره: پشتیبانی از چندین حساب کاربری و سطوح دسترسی

- **ویژگی‌های فنی**
  - یکپارچه‌سازی داکر: پشتیبانی کامل از کانتینرسازی با داکر
  - یکپارچه‌سازی Nginx: پیکربندی پیشرفته وب سرور با Nginx
  - گواهینامه SSL: راه‌اندازی و تمدید خودکار گواهینامه SSL
  - مدیریت نود: افزودن و پیکربندی آسان نودهای جدید
  - یکپارچه‌سازی تلگرام: ربات تلگرام داخلی برای اعلان‌ها و کنترل

- **تجزیه و تحلیل و گزارش‌گیری**
  - تحلیل ترافیک: نظارت و تحلیل دقیق ترافیک
  - آمار استفاده: آمار و گزارش‌های جامع استفاده
  - ردیابی کاربر: نظارت بر فعالیت‌ها و اتصالات کاربران
  - گزارش‌های سیستم: گزارش‌های دقیق سیستم برای عیب‌یابی

- **ویژگی‌های اضافی**
  - پشتیبانی چند زبانه: رابط کاربری در زبان‌های مختلف
  - به‌روزرسانی‌های منظم: به‌روزرسانی و بهبود مداوم سیستم
  - دسترسی ۲۴/۷: طراحی شده برای عملکرد مداوم
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

4. اجرای اسکریپت برای تولید کدهای JWT:
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

9. جایگزینی مقادیر پیش‌فرض با مقادیر صحیح:
```env
### APP ###
APP_PORT=3000

DATABASE_URL="postgresql://postgres:postgres@remnawave-db:5432/postgres"

### JWT ###
### تغییر مقادیر پیش‌فرض ###
JWT_AUTH_SECRET=کد_هگز_اول_شما
JWT_API_TOKENS_SECRET=کد_هگز_دوم_شما

### TELEGRAM ###
TELEGRAM_BOT_TOKEN=توکن_ربات_تلگرام_شما
TELEGRAM_ADMIN_ID=آیدی_ادمین_تلگرام_شما
NODES_NOTIFY_CHAT_ID=آیدی_چت_تلگرام_شما

### FRONT_END ###
FRONT_END_DOMAIN=*

### SUBSCRIPTION ###
SUB_SUPPORT_URL=https://زیردامنه_شما
SUB_PROFILE_TITLE=پروفایل اشتراک
SUB_UPDATE_INTERVAL=12
SUB_WEBPAGE_URL=https://زیردامنه_شما

### SUBSCRIPTION PUBLIC DOMAIN ###
### دامنه خام، بدون HTTP/HTTPS، بدون / در انتها ###
SUB_PUBLIC_DOMAIN=rw.guilanit.com

EXPIRED_USER_REMARKS=["اشتراک منقضی شده","با پشتیبانی تماس بگیرید"]
DISABLED_USER_REMARKS=["اشتراک غیرفعال شده","با پشتیبانی تماس بگیرید"]
LIMITED_USER_REMARKS=["اشتراک محدود شده","با پشتیبانی تماس بگیرید"]

### SUPERADMIN ###
### تغییر مقادیر پیش‌فرض ###
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
### فقط https:// مجاز است ###
WEBHOOK_URL=https://webhook.site/1234567890
### این رمز برای امضای محتوای webhook استفاده می‌شود، باید دقیقاً 64 کاراکتر باشد. فقط a-z، 0-9، A-Z مجاز هستند ###
WEBHOOK_SECRET_HEADER=vsmu67Kmg6R8FjIOF1WUY8LWBHie4scdEqrfsKmyf4IAf8dY3nFS0wwYHkhh6ZvQ

### CLOUDFLARE ###
# فقط برای docker-compose-prod-with-cf.yml استفاده می‌شود
# توسط خود برنامه استفاده نمی‌شود
CLOUDFLARE_TOKEN=ey...

### Database ###
### برای کانتینر Docker Postgres ###
# توسط خود برنامه استفاده نمی‌شود
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

### دستورالعمل‌های راه‌اندازی نود

پس از نصب پنل اصلی، یک سرور مجازی جدید با موقعیت مورد نظر خود ایجاد کنید.

1. ابتدا Docker را روی سرور خود نصب کنید:
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
su
