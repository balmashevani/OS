# Лабораторная работа №5

Имеется четыре виртуальные машины :

* web1
* web2
* haproxy1
* haproxy2

## Задание

 * На серверах web1, web2 установить Nginx.
 * На серверах haproxy1, haproxy2 установить и настроить отказоустойчивую связку HAProxy+Keepalived. Настроить VIP с помощью Keepalived в соответствии со схемой
 * На серверах web1, web2 Nginx должен генерировать кастомную страницу, зайдя на которую можно понять на каком сервере вы находитесь.
 * На серверах с HAProxy ПО должно обеспечить балансировку нагрузки серверов web1 и web2 в режиме round-robin. 
 * Установка и настройка всего ПО должна быть обеспечена Ansible-сценарием.
 * Все файлы по этому заданию выложить в Github и написать ReadMe со скринами.

## Запуск playbook

Сначала уничтожить все то, что было сделано:

````
vagrant destroy --force
````

Далее поднять vagrant:
````
vagrant up
````


### Далее появляется куча ошибок🙃🙃🙃🙃🙃🙃🙃🙃


Никита Андреевич вводит волшебные команды, и все начинает работать✨


### Затем появляется моя любимая ошибка)))))))))))))))))))))))))))))))))))))))))))))


Вводим команды:

````
sudo ip link set vboxnet0 up
````

````
sudo ip addr add 192.168.11.1/24 dev vboxnet0
````


Возвращаемся к playbook:

````
ansible-playbook nginx.yml 
````


## Проверка балансировщика


<a href="https://ibb.co/sFMCFTy"><img src="https://i.ibb.co/rZ13ZB4/web1.png" alt="web1" border="0"></a>


<a href="https://ibb.co/BTRPMhZ"><img src="https://i.ibb.co/HGQ28cz/web2.png" alt="web2" border="0"></a>


<a href="https://ibb.co/d0Dwhw3"><img src="https://i.ibb.co/7JKd9dT/all-running.png" alt="all-running" border="0"></a>


## Проверка отказоустойчивости


### Отключен haproxy1


<a href="https://ibb.co/sFMCFTy"><img src="https://i.ibb.co/rZ13ZB4/web1.png" alt="web1" border="0"></a>


<a href="https://ibb.co/BTRPMhZ"><img src="https://i.ibb.co/HGQ28cz/web2.png" alt="web2" border="0"></a>


<a href="https://ibb.co/gmRdf8F"><img src="https://i.ibb.co/bQKFCVR/off1.png" alt="off1" border="0"></a>


### Отключен haproxy2


<a href="https://ibb.co/sFMCFTy"><img src="https://i.ibb.co/rZ13ZB4/web1.png" alt="web1" border="0"></a>


<a href="https://ibb.co/BTRPMhZ"><img src="https://i.ibb.co/HGQ28cz/web2.png" alt="web2" border="0"></a>


<a href="https://ibb.co/6ZjJWvR"><img src="https://i.ibb.co/3sgYCfy/off2.png" alt="off2" border="0"></a>
