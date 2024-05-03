# VRRP + HAproxy + Nginx

Отказоустойчивый стенд с двумя балансировщиками HAProxy с VRRP, за которыми стоят два веб-сервера Nginx

## Как запускать
```
vagrant up
```
## Ansible Playbooks

```
cd provision
ansible-playbook playbooks/environment.yml
```
## Хосты

- [lb] 
    - haproxy1 (10.0.26.201)
    - haproxy2 (10.0.26.202)
- [webapp]
    - web1 (10.0.26.101)
    - web2 (10.0.26.102)


# Доступ к веб-интерфейсу

## VIP access
http://10.0.26.81

http://10.0.26.81:8080/stats

## Веб-серверы

web1: http://10.0.26.201

web2: http://10.0.26.202

## Балансировщики

lb1: http://10.0.26.101

lb2: http://10.0.26.102

### Страница статистики HAProxy

http://127.0.0.1:8080/stats

* логин: stat
* пароль: statpass

## Версии
* OS: Ubuntu 22.04
* HAProxy: 2.8 (PPA)
* Keepalived: 2.2.4