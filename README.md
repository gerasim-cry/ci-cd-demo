## CI/CD + Monitoring Demo

Здесь собрана минимальная, но полноценная инфраструктура на базе Docker, с автосборкой через GitHub Actions, экспортом метрик в Prometheus и автоматическим подключением дашборда в Grafana. Всё сделано на простой Flask-программе, чтобы сконцентрироваться именно на пайплайне и мониторинге.

## Состав проекта

- Flask API — минимальное приложение на Python, отдаёт метрики

- Docker — все сервисы запускаются в контейнерах

- GitHub Actions — CI-пайплайн с проверкой сборки

- Prometheus — забирает метрики с приложения

- Grafana — визуализирует метрики, подключает дашборд автоматически

- Loki + Promtail — сбор и просмотр логов контейнеров в Grafana

## Запуск

# Клонировать репозиторий
https://github.com/gerasim-cry/ci-cd-demo.git
cd ci-cd-demo

# Запуск контейнеров
docker-compose up --build
 
## Доступ по адресам:

API: http://localhost:5000

Метрики: http://localhost:5000/metrics

Prometheus: http://localhost:9090

Grafana: http://localhost:3000 
(логин: admin / admin)

Loki API: http://localhost:3100

## Что показывает дашборд

- Количество HTTP-запросов

- Статус и доступность приложения

- Просмотр логов приложения (через Loki)

- Лежит в папке DevOps Demo внутри Grafana

JSON-файл с дашбордом: grafana/dashboards/ci-cd-dashboard.json

## Что здесь полезного

- Основы CI/CD с GitHub Actions

- Prometheus + Flask = экспорт собственных метрик

- Grafana настроена через provisioning — дашборд появляется сразу

- Работа с volumes, правами доступа и SELinux в Fedora

- Чтение логов из Docker-контейнеров через Promtail + Loki

- Настройка визуализации логов через панель в Grafana
