# Лабораторная работа: Развертывание кластера K3s

## Описание
Развертывание кластера Kubernetes на базе K3s с использованием LXD контейнеров.

## Архитектура
- **Master node**: ubuntuu (хостовая машина)
- **Worker nodes**: node1, node2 (LXD контейнеры)
- **Сеть**: LXD bridge (10.3.51.0/24)

## Шаги выполнения

### 1. Подготовка инфраструктуры
- Созданы LXD контейнеры: ctrl, node1, node2
- Настроены лимиты ресурсов (memory: 3GiB для ctrl, 1.5GiB для node1/node2)
- Загружены модули ядра: br_netfilter, overlay

### 2. Установка K3s Server на хосте
```bash
curl -sfL https://get.k3s.io | sudo sh -s - \
  --disable=traefik \
  --disable=servicelb \
  --disable=metrics-server \
  --tls-san=10.3.51.1 \
  --write-kubeconfig-mode=644
