# Лабораторная работа №5

pg01 and pg02, на каждом из которых работает:

* PostgreSQL
* Patroni
* Consul agent

1. Установили и настроили консул.

````
ansible-playbook consul.play
````

2. Проинициализировали БД на выделенных дисках. БД находится в папке /pgsql/pg_data/14. WAL архивы находится в папке /pgsql/pg_wal/14. В эти папки примонтированы диски /dev/sdb и /dev/sdc соответственно. Диски подключены в LVM и отформатированы в файловой системе xfs.

````
vgcreate pgdata /dev/sdb
vgcreate pgwal /dev/sdc
````

````
lvcreate -l+100%FREE -n pgdata pgdata
lvcreate -l+100%FREE -n pgwal pgwal
````

````
mkfs.xfs /dev/mapper/pgdata-pgdata
mkfs.xfs /dev/mapper/pgwal-pgwal
````

3. На серверах pg1 и pg2 настроить оркестратор репликации Patroni.

````
yum install patroni-2.0.2-1.rhel7.x86_64.rpm
````


4. С помощью утилиты vip-manager обеспечили настройку VIP адреса на мастер сервере. 

````
yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
````

# Проверка, что все шииикарнноо работает (наконец-то!)

* Cносим все нафиг, а для чего же мы еще это так долго делали

````
vagrant desroy --force
````

* Запускаем виртуалку

````
vagrant up
```` 

* Запускаем чудесный-расчудесный playbook (плэй - играть, бук - книга)

````
ansible-playbook playbook.yml
````

# Ваууу звуки восторга и зеленой ячейки в табличке
