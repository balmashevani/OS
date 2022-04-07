# Лабораторная работа №5

Имеется четыре виртуальные машины :

* web1
* web2
* haproxy1
* haproxy2

## Задание

 + На серверах web1, web2 установить Nginx.
 + На серверах haproxy1, haproxy2 установить и настроить отказоустойчивую связку HAProxy+Keepalived. Настроить VIP с помощью Keepalived в соответствии со схемой
 + На серверах web1, web2 Nginx должен генерировать кастомную страницу, зайдя на которую можно понять на каком сервере вы находитесь.
 + На серверах с HAProxy ПО должно обеспечить балансировку нагрузки серверов web1 и web2 в режиме round-robin. 
 + Установка и настройка всего ПО должна быть обеспечена Ansible-сценарием.
 + Все файлы по этому заданию выложить в Github и написать ReadMe со скринами.

## Запуск playbook

Сначала уничтожить все то, что было сделано:

````
vagrant destroy --force
````

Далее поднять vagrant:
````
vagrant up
````

### Далее появляется куча ошибок

Никита Андреевич вводит волшебные команды, и все начинает работать✨

### Затем появляется моя любимая ошибка)))))))))))))))))))))))))))))))))))))))))))))


Вводим команды:

````
sudo ip link set vboxnet0 up
````

````
sudo ip addr add 192.168.11.1/24 dev vboxnet0
````

Возвращаемся playbook:

````
ansible-playbook nginx.yml 
````

## Проверка балансировщика
### Всё прекрасно
![всё прекрасно](https://github.com/naaastyazharkova/Operating-System/blob/lab-05/lab5_os/pictures/ha1%2B2.png)


## Проверка отказоустойчивости
### Отключен haproxy1
![отключен haproxy1](https://github.com/naaastyazharkova/Operating-System/blob/lab-05/lab5_os/pictures/ha2.png)

### Отключен haproxy2
![отключен haproxy2](https://github.com/naaastyazharkova/Operating-System/blob/lab-05/lab5_os/pictures/ha1.png)
