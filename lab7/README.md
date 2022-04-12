postgresql-patroni-setup
Обзор
This repo it helps you quickly spin up a 3-node cluster of PostgreSQL, managed by Patroni using Consul.

What's in the cluster?
When you start the cluster, you get 2 nodes (pg01 and pg02), each running:

PostgreSQL
Patroni
Consul agent

1. Установили и настроили консул.
ansible-playbook consul.play
2. Проинициализировали БД на выделенных дисках. 
ansible-playbook playbook.yml
БД находится в папке /pgsql/pg_data/14. WAL архивы находится в папке /pgsql/pg_wal/14. В эти папки примонтированы диски /dev/sdb и /dev/sdc соответственно. Диски подключены в LVM и отформатированы в файловой системе xfs.
3. На серверах pg1 и pg2 настроить оркестратор репликации Patroni.
4. С помощью утилиты vip-manager обеспечить настройку VIP адреса на мастер сервере. https://github.com/cybertec-postgresql/vip-manager/releases/download/v1.0.2/vip-manager-1.0.2-1.x86_64.rpm . Напоминаю, что в конфиге vip-manager необходимо настроить подключение по DCS Consul. IP адрес подключения 127.0.0.1:8500. Так же нужно будет указать consul_token, переменную которого можно взять в роли consul