<div align="center">
  <h1 style="color: #00bcd4;">Remnawave 自动安装程序</h1>
  <p>用于在 Linux 上自动安装 Remnawave 面板和节点连接的专业脚本</p>
  <img src="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/52637e61cc545ce5b096ea3359758b4629451c96/remnawave_screenshot.png?raw=true" alt="Remnawave 截图" style="width: 80%; max-width: 800px; margin: 20px 0;">
  
  <!-- 许可证、版本和平台徽章 -->
  <div style="display: flex; justify-content: center; gap: 15px; margin-top: 20px;">
    <img src="https://img.shields.io/badge/Platform-Linux-brightgreen" alt="Linux">
    <img src="https://img.shields.io/badge/Version-v0.1%20(Beta)-orange" alt="Version">
    <img src="https://img.shields.io/badge/License-MIT-blue" alt="MIT License">
  </div>

  <br><br>
  <div style="font-size: 14px;">
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/blob/main/README.md" style="text-decoration: none; color: #007bff;">English</a> | 
    <a href="[#](https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-fa.md)" style="text-decoration: none; color: #007bff;">فارسی</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-ru.md" style="text-decoration: none; color: #007bff;">Русский</a> | 
    <a href="https://github.com/AsanFillter/Remnawave-AutoSetup/docs/docs/README-zh.md/" style="text-decoration: none; color: #007bff;">中文</a>
  </div>
</div>

## 系统要求

- Ubuntu 20.04 或更高版本
- 最少 1GB 内存
- 10GB 可用磁盘空间
- 服务器 root 访问权限
- 有效域名（用于 SSL）
- 域名已指向您的服务器 IP

## 功能特点

- **安全性**
  - 高级加密：最先进的加密协议，确保最大安全性
  - 防攻击系统：内置 DDoS 和其他网络攻击防护
  - IP 隐藏：高级 IP 掩码和保护功能
  - 多层安全：多重安全层保护您的数据

- **性能**
  - 高速性能：优化以实现最大速度和最小延迟
  - 负载均衡：智能流量分配到多个节点
  - 无限带宽：无数据传输限制
  - 全球网络：访问全球服务器

- **管理**
  - 简易面板管理：用户友好的界面，便于管理
  - 实时监控：实时监控所有连接和流量
  - 自动配置：自动安装和配置
  - 多用户系统：支持多个用户账户和权限

- **技术特性**
  - Docker 集成：使用 Docker 实现完整容器化
  - Nginx 集成：使用 Nginx 进行高级 Web 服务器配置
  - SSL 证书：自动 SSL 证书设置和更新
  - 节点管理：轻松添加和配置新节点
  - Telegram 集成：内置 Telegram 机器人用于通知和控制

- **分析和报告**
  - 流量分析：详细的流量监控和分析
  - 使用统计：全面的使用统计和报告
  - 用户跟踪：监控用户活动和连接
  - 系统日志：详细的系统日志用于故障排除

- **附加功能**
  - 多语言支持：界面支持多种语言
  - 定期更新：持续的系统更新和改进
  - 24/7 运行：设计用于持续运行
  - 备份系统：自动备份和恢复功能

> **注意**：需要 Ubuntu 20.04 或更高版本。

---

### 自动安装

在终端中运行以下命令以自动安装 Remnawave：

```sh
curl -s https://raw.githubusercontent.com/AsanFillter/Remnawave-AutoSetup/dfe140d1cb758bbc9f7f4485977b4d65ff5833f9/install_remnawave.sh | bash
```

<details>
<summary><b>手动安装</b></summary>

### 面板安装步骤

1. 安装必要组件：
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. 创建新文件 `jwtgen.py`：
```sh
nano jwtgen.py
```

3. 将以下内容添加到 `jwtgen.py`：
```python
import secrets

# 生成 JWT_AUTH_SECRET
jwt_auth_secret = secrets.token_hex(32)
print("JWT_AUTH_SECRET:", jwt_auth_secret)

# 生成 JWT_API_TOKENS_SECRET
jwt_api_tokens_secret = secrets.token_hex(32)
print("JWT_API_TOKENS_SECRET:", jwt_api_tokens_secret)
```

4. 运行脚本生成 JWT 密钥：
```sh
python3 jwtgen.py
```

5. 保存生成的十六进制代码以供后用。

6. 创建 Remnawave 目录并进入：
```sh
mkdir remnawave && cd remnawave
```

7. 下载项目配置文件：
```sh
curl -o .env https://raw.githubusercontent.com/remnawave/backend/refs/heads/main/.env.sample
```

8. 编辑配置文件：
```sh
nano .env
```

9. 将占位符替换为正确的值：
```env
### APP ###
APP_PORT=3000

DATABASE_URL="postgresql://postgres:postgres@remnawave-db:5432/postgres"

### JWT ###
### 更改默认值 ###
JWT_AUTH_SECRET=您的第一个十六进制码
JWT_API_TOKENS_SECRET=您的第二个十六进制码

### TELEGRAM ###
TELEGRAM_BOT_TOKEN=您的Telegram机器人令牌
TELEGRAM_ADMIN_ID=您的Telegram管理员ID
NODES_NOTIFY_CHAT_ID=您的Telegram聊天ID

### FRONT_END ###
FRONT_END_DOMAIN=*

### SUBSCRIPTION ###
SUB_SUPPORT_URL=https://您的子域名
SUB_PROFILE_TITLE=订阅配置
SUB_UPDATE_INTERVAL=12
SUB_WEBPAGE_URL=https://您的子域名

### SUBSCRIPTION PUBLIC DOMAIN ###
### 原始域名，无需 HTTP/HTTPS，域名末尾不要加 / ###
SUB_PUBLIC_DOMAIN=rw.guilanit.com

EXPIRED_USER_REMARKS=["订阅已过期","联系支持"]
DISABLED_USER_REMARKS=["订阅已禁用","联系支持"]
LIMITED_USER_REMARKS=["订阅受限","联系支持"]

### SUPERADMIN ###
### 更改默认值 ###
SUPERADMIN_USERNAME=您的管理员用户名
SUPERADMIN_PASSWORD=您的管理员密码

### SWAGGER ###
SWAGGER_PATH=/docs
SCALAR_PATH=/scalar
IS_DOCS_ENABLED=true

### PROMETHEUS ###
METRICS_USER=admin
METRICS_PASS=admin

### WEBHOOK ###
WEBHOOK_ENABLED=true
### 仅允许 https:// ###
WEBHOOK_URL=https://webhook.site/1234567890
### 此密钥用于签名 webhook 负载，必须为64个字符。仅允许 a-z, 0-9, A-Z ###
WEBHOOK_SECRET_HEADER=vsmu67Kmg6R8FjIOF1WUY8LWBHie4scdEqrfsKmyf4IAf8dY3nFS0wwYHkhh6ZvQ

### CLOUDFLARE ###
# 仅用于 docker-compose-prod-with-cf.yml
# 应用程序本身不使用
CLOUDFLARE_TOKEN=ey...

### Database ###
### 用于 Postgres Docker 容器 ###
# 应用程序本身不使用
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=postgres
```

10. 创建 Docker Compose 文件：
```sh
nano docker-compose.yml
```

11. 将以下内容添加到 `docker-compose.yml`：
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

12. 运行以下命令启动容器：
```sh
docker compose up -d
```

13. 检查日志确保一切运行正常：
```sh
docker compose logs -f
```

### 节点设置说明

安装主面板后，使用您想要的位置创建一个新的虚拟服务器。

1. 首先，在服务器上安装 Docker：
```sh
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install -y docker-ce
docker --version
```

2. 更新服务器：
```sh
sudo apt update && apt upgrade -y
```

3. 创建节点目录并创建 Docker 文件：
```sh
mkdir /remnanode && cd /remnanode && nano docker-compose.yml
```

4. 将以下内容添加到 `docker-compose.yml`：
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

5. 创建并编辑 .env 文件：
```sh
nano .env
```

6. 转到您的面板并添加节点。点击"重要信息"并复制密钥。将其添加到您的 .env 文件中：
```env
### APP ###
APP_PORT=2222
```

7. 启动 Docker 容器并检查日志：
```sh
docker compose up -d && docker compose logs -f
```

</details>

## 贡献

欢迎各种形式的贡献！以下是您可以帮助的方式：

- 报告错误或问题
- 提出新功能建议
- 改进文档
- 审查代码更改

## 支持

如果您觉得这个项目有用，请考虑在 GitHub 上给它一个星！

- **Telegram 频道：** [@AsanFillter](https://t.me/AsanFillter)  
- **Telegram 群组：** [@AsanFillter_Group](https://t.me/asanfillter_group)

更多信息和文档，请访问 [Remnawave 官方网站](https://remnawave.com)。
