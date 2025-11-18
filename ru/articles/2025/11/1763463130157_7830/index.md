---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'MariaDB: Пользователи'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'mariadb'
tags:
  - 'mariadb'
  - 'user'
authors:
  - 'KaiKimera'
sources:
  - ''
license: 'CC-BY-SA-4.0'
complexity: '0'
toc: 1
comments: 1

# -------------------------------------------------------------------------------------------------------------------- #
# DATE
# -------------------------------------------------------------------------------------------------------------------- #

date: '2025-11-18T13:52:10+03:00'
publishDate: '2025-11-18T13:52:10+03:00'
lastMod: '2025-11-18T13:52:10+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: 'cf00d3f08910a83b633705ec66347f04d274865f'
uuid: 'cf00d3f0-8910-583b-9337-05ec66347f04'
slug: 'cf00d3f0-8910-583b-9337-05ec66347f04'

draft: 1
---

Работа с пользователями в {{< tag "MariaDB" >}}.

<!--more-->

- Посмотреть список пользователей:

```bash
echo 'select user, host, password from mysql.user;' | mariadb --user='root' --password
```

- Создать пользователя `DB_USER` с паролем `DB_PASSWORD`:

```bash
echo "create user 'DB_USER'@'127.0.0.1' identified by 'DB_PASSWORD';" | mariadb --user='root' --password
```

- Переименовать пользователя `DB_USER@127.0.0.1` в `DB_USER@localhost`:

```bash
echo "rename user 'DB_USER'@'127.0.0.1' to 'DB_USER'@'localhost';" | mariadb --user='root' --password
```

- Изменить пароль пользователя `DB_USER` на `DB_PASSWORD_NEW`:

```bash
echo "alter user 'DB_USER'@'127.0.0.1' identified by 'DB_PASSWORD_NEW';" | mariadb --user='root' --password
```

- Удалить пользователя `DB_USER`:

```bash
echo "drop user 'DB_USER'@'127.0.0.1';" | mariadb --user='root' --password
```

- Дать права `CREATE`, `ALTER`, `DROP`, `INSERT`, `UPDATE`, `DELETE`, `SELECT`, `REFERENCES` и `RELOAD` на базу данных `DB_NAME` пользователю `DB_USER`:

```bash
echo "grant create, alter, drop, insert, update, delete, select, references, reload on DB_NAME.* to 'DB_USER'@'127.0.0.1'; flush privileges;" | mariadb --user='root' --password
```

- Дать все права на базу данных `DB_NAME` пользователю `DB_USER`:

```bash
echo "grant all on DB_NAME.* to 'DB_USER'@'127.0.0.1'; flush privileges;" | mariadb --user='root' --password
```

- Дать все права на все базы данных пользователю `DB_USER`:

```bash
echo "grant all on *.* to 'DB_USER'@'127.0.0.1'; flush privileges;" | mariadb --user='root' --password
```

- Отозвать все права пользователя `DB_USER` у базы данных `DB_NAME`:

```bash
echo "revoke all on DB_NAME from 'DB_USER'@'127.0.0.1';" | mariadb --user='root' --password
```

- Показать права пользователя `DB_USER`:

```bash
echo "show grants for 'DB_USER'@'127.0.0.1';" | mariadb --user='root' --password
```
