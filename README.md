#  CI/CD Demo Project 
Пример DevOps-проекта с автоматизацией процессов разработки и деплоя. 
Включает в себя базовое веб-приложение на Flask, контейнеризацию с Docker и CI/CD через GitHub Actions. 

--- 

## Технологии 
- **Python 3.11 + Flask** — простое API-приложение 
- **Docker / Docker Compose** — упаковка и локальный запуск 
- **GitHub Actions** — CI-пайплайн: проверка, сборка 
- **act** — локальное тестирование GitHub Actions 

--- 

## Структура проекта
ci-cd-demo/
├──app/ 
│   ├──app.py              # Flask-приложение
│   └──requirements.txt    # Зависимости
├──Dockerfile              # Инструкция сборки контейнера
├──docker-compose.yml      # Локальный запуск
├──.dockerignore           # Исключения из сборки
├──.gitignore              # Исключения для Git
├──.github/
│   └──workflows/
│       └──ci.yml          # CI/CD конфигурация
├──README.md

---

## Локальный запуск

docker-compose up --build

Открыть в браузере: http://localhost:5000

---

## CI/CD Workflow (GitHub Actions)

При каждом git push в ветку main GitHub запускает CI:
1. Клонирует репозиторий
2. Устанавливает Python и зависимости
3. Проверяет, что Flask-приложение запускается
4. Собирает Docker-образ

Конфигурация: .github/workflows/ci.yml

---

## Локальный запуск CI (с act)

Чтобы не ждать GitHub, можно запускать CI/CD у себя:

1. Установка act:
curl -s https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash
2. Запуск:
act --privileged
Параметр --privileged нужен для доступа к Docker внутри CI-контейнера
