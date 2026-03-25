# Домашнее задание к занятию 1 «Disaster recovery и Keepalived»
**Выполнил:** Чехлов Михаил


## Задание 1

### Настройки раннера

![Страница Settings → CI/CD → Runners]
*Статус раннера — active (зелёная точка), теги: `docker`, `ubuntu`.*

![Вывод команды gitlab-runner list]
*Раннер зарегистрирован с ID #1 (`5vm1Sof3W`).*

## Задание 2

### Статус раннера и теги

![Страница Settings → CI/CD → Runners]
*Статус раннера — active (зелёная точка), теги: `docker`, `ubuntu`.*

### Вывод команд статуса

![Вывод команд gitlab-runner status, git status]
*Раннер зарегистрирован с ID #2 (`2bxg3Mjny`).*

### Логи выполнения пайплайна


![Логи задания test-pipeline]
*Вывод команд: `echo`, `uname -a`, `whoami`.*


## Конфигурация GitLab CI/CD

Содержимое файла `gitlab-ci.yml`:


```yaml
test-docker:
  tags:
    - docker
  script:
    - echo "Running in Docker container!"  # Тестовый вывод
    - docker --version                  # Версия Docker
    - uname -a                         # Информация о системе
    - whoami                         # Текущий пользователь
