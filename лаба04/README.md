Лабораторная работа №4
Виртуальные машины:

web1

web2

rrobin

!Сервера web1 и web2 должны генерировать кастомную страницу, а robbin будет настраивать балансировку нагрузки этих серверов в режиме round-robin

Что нужно сделать:
1)На серверах web1, web2, rrobin установить nginx
2)Сервера web1 и web2 должны работать по порту 8080
3)Выполнить балансировку серверов web1 и web2
4)Создать playbook в котором мы расписываем роли webserves (web1, web2) и rrobin

Команды:

-поднимаем виртуалки
`vagrant up`

-(у меня выходила ошибка, поэтому я использовала еще и след. команды)
`sudo ip link set vboxnet0 up`
`sudo ip addr add 192.168.11.1/24 dev vboxnet0`

<a href="https://ibb.co/4gYS0XS"><img src="https://i.ibb.co/h1ZdT4d/image.png" alt="image" border="0"></a>

-запуск playbook
`ansible-playbook nginx.yml`

Кастомные страницы:

Кастомная страница web1

<a href="https://ibb.co/YhqDY8j"><img src="https://i.ibb.co/zZ08jbf/1.png" alt="1" border="0"></a>

Кастомная страница web2

<a href="https://ibb.co/rx5Q3f0"><img src="https://i.ibb.co/c62ywX3/2.png" alt="2" border="0"></a>
