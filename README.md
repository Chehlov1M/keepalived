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


## Настройка VIP в Keepalived

Содержимое файла `/etc/keepalived/keepalived.conf`:

VM1 (MASTER):
```conf
vrrp_instance VI_1 {
    state BACKUP
    interface eth0
    virtual_router_id 15
    priority 255
    nopreempt

    virtual_ipaddress {
        192.168.111.15/24 dev eth0
    }
}

```
VM2 (BACKUP):
```conf
vrrp_instance VI_1 {
    state BACKUP
    interface eth0
    virtual_router_id 15
    priority 100
    nopreempt

    virtual_ipaddress {
        192.168.111.15/24 dev eth0
    }
}

