# Отчет по лабораторной работе: Установка Git и Docker

## Цель
Изучить и выполнить установку Git и Docker на операционной системе Linux.

## Шаги выполнения

### 1. Установка Git
- Выполнена команда для обновления пакетов:
  ```bash
  sudo apt update
  ```
- Установлен Git:
  ```bash
  sudo apt install git
  ```
- Проверена версия Git:
  ```bash
  git --version
  ```

### 2. Установка Docker
- Установлены необходимые зависимости:
  ```bash
  sudo apt install apt-transport-https ca-certificates curl software-properties-common
  ```
- Добавлен Docker GPG ключ:
  ```bash
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  ```
- Добавлен репозиторий Docker:
  ```bash
  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  ```
- Установлен Docker:
  ```bash
  sudo apt install docker-ce
  ```
- Проверена версия Docker:
  ```bash
  docker --version
  ```

### 3. Тестирование установки Docker
- Запущен тестовый контейнер:
  ```bash
  sudo docker run hello-world
  ```
  Контейнер успешно запущен и выведено сообщение о корректной работе Docker.

## Результат
Git и Docker успешно установлены. Проведены базовые тесты на работоспособность Docker.

## Вывод
Данная лабораторная работа помогла освоить базовые шаги по установке и настройке Git и Docker на системе Linux.
