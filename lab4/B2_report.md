# Отчёт по заданию B2: Molecule

## 1. Что такое Molecule и зачем он нужен?
Molecule — фреймворк для автоматического тестирования Ansible-ролей. Создаёт временные контейнеры, применяет роль, проверяет результат через testinfra, удаляет контейнеры. Гарантия качества, регрессионное тестирование, мультиплатформенность.

## 2. Какие этапы проходит Molecule?
dependency, lint, cleanup, create, prepare, converge, idempotence, verify, cleanup, destroy.

## 3. Что такое testinfra?
Python-библиотека для тестирования инфраструктуры в стиле pytest. Проверяет состояние системы: установлены ли пакеты, запущены ли сервисы, открыты ли порты.

## 4. Почему важно тестировать на разных ОС?
Разные пакетные менеджеры (apt, yum, apk), разные пути к конфигам, разные имена сервисов, разные версии systemd и пакетов.

## 5. Как интегрировать Molecule в GitLab CI?
Использовать docker:dind (Docker-in-Docker):
- image: python:3.12
- services: docker:24-dind
- script: pip install molecule molecule-plugins[docker] testinfra && molecule test
