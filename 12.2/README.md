# Домашнее задание к занятию "Работа с данными (DDL/DML)" - Екимовский К.

### Задание №1

- Список пользователей:


- Список прав пользователя sys_temp:


- Восстановление БД sakila:

```
SOURCE /root/sakila-db/sakila-schema.sql 
SOURCE /root/sakila-db/sakila-data.sql
``` 

ER-диаграмма: 

Запросы:

```

CREATE user 'sys_temp'@'%' identified by '7856';
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'%';
SELECT user FROM mysql.user;
SHOW GRANTS FOR 'sys_temp'@'%';
SOURCE /root/sakila-db/sakila-schema.sql
SOURCE /root/sakila-db/sakila-data.sql
SHOW DATABASES;
USE sakila;
SHOW FULL TABLES;

```

### Задание №2

Запросы:

```

USE sakila;
SHOW FULL TABLES;

SELECT k.column_name
FROM information_schema.table_constraints t
JOIN information_schema.key_column_usage k
USING(constraint_name,table_schema,table_name)
WHERE t.constraint_type='PRIMARY KEY'
  AND t.table_schema='sakila';

```

Скриншот с ключами: 


### Задание №3

Так как мы не давали пользователю sys_temp прав на БД sakila (изначально дали на все БД и таблицы), то и забрать права именно на БД sakila не получиться.
Поэтому сначала нужно дать права, затем забрать:

```

GRANT ALL PRIVILEGES ON sakila.* TO `sys_temp`@`%`;
REVOKE INSERT, DELETE, UPDATE ON sakila.* FROM `sys_temp`@`%`;
REVOKE INSERT, DELETE, UPDATE ON *.* FROM `sys_temp`@`%`;

```

Скриншоты:


