# 📦 WABA (WhatsApp Business API) – интеграция с CRM и чатами
### Проект предназначен для приёма и отправки сообщений через WhatsApp Business API (WABA) с интеграцией в сторонние CRM (например, amoCRM), включая:
- хранение истории сообщений
- маршрутизацию сообщений
- WebSocket-уведомления
- Поддержка очередей через RabbitMQ
---
## 🚀 Быстрый старт
### 🔧 Требования
- Python 3.12+
- Docker и Docker Compose
- PostgreSQL
- Redis
- RabbitMQ
---
## 🐳 Запуск в Docker
```bash
  docker-compose up -d --build
```
### Проверить логи приложения:
```bash
  docker-compose logs app
```
---
## 📁 Структура проекта
```
waba_api/
├── main.py                  # Точка входа в FastAPI
├── docker-compose.yml       # Конфигурация Docker
├── Dockerfile               # Сборка образа
├── requirements.txt         # Зависимости
├── .env*                    # Переменные окружения
├── src/
│   ├── api/                 # FastAPI роутеры (amoCRM, Meta, RabbitMQ)
│   ├── database/
│   │   ├── models/          # SQLAlchemy модели
│   │   ├── migrations/      # Alembic миграции
│   ├── utils/               # Подключение к Redis, RMQ, логи
│   ├── settings/            # Конфигурация приложения
```
---
## 🧠 Возможности
- Обработка входящих сообщений от Meta API
- Отправка событий в amoCRM
- История сообщений по связке клиент-оператор
- WebSocket интеграция для уведомлений
- Очереди RabbitMQ
- Redis кэш
- Alembic миграции базы данных
---
## 🛠️ Миграции Alembic
```bash
    docker-compose run alembic alembic revision --autogenerate -m "your message"
```
```bash
  docker-compose run alembic alembic upgrade head
```
---
## 📡 Переменные окружения
- .env — основные переменные
- .env.redis — конфигурация Redis
- .env.rmq — конфигурация RabbitMQ
- .env.chat, .env.amo, .env.meta — доступы к внешним API

Пример .env:
```dotenv
POSTGRES_DB=waba
POSTGRES_USER=admin
POSTGRES_PASSWORD=secret
```
---
### 🧩 Стек технологий
- FastAPI
- SQLAlchemy 2.0
- Alembic
- PostgreSQL
- Redis
- RabbitMQ (aio-pika)
- Docker
---
