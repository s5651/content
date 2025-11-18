---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'MariaDB: Импорт'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'mariadb'
tags:
  - 'mariadb'
  - 'import'
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

date: '2025-11-18T13:52:14+03:00'
publishDate: '2025-11-18T13:52:14+03:00'
lastMod: '2025-11-18T13:52:14+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: '5843128cc1c34623ce3bb5c0f1f39478ff736bbb'
uuid: '5843128c-c1c3-5623-8e3b-b5c0f1f39478'
slug: '5843128c-c1c3-5623-8e3b-b5c0f1f39478'

draft: 1
---

Работа с импортом баз данных в {{< tag "MariaDB" >}}.

<!--more-->

- Удалить старую базу данных `DB_NAME`:

```bash
echo 'drop database if exists DB_NAME;' | mariadb --user='root' --password
```

- Создать базу данных `DB_NAME` с кодировкой `utf8mb4` и сопоставлением `utf8mb4_unicode_ci`:

```bash
echo "create database if not exists DB_NAME character set 'utf8mb4' collate 'utf8mb4_unicode_ci';" | mariadb --user='root' --password
```

- Дать все права на базу данных `DB_NAME` пользователю `DB_USER`:

```bash
echo "grant all privileges on DB_NAME.* to 'DB_USER'@'127.0.0.1'; flush privileges;" | mariadb --user='root' --password
```

- Импортировать данные в новую базу данных `DB_NAME` из файла `DB_NAME.sql.xz`:

```bash
d='DB_NAME'; f="${d}.sql"; xz -d "${f}.xz" && mariadb --user='root' --password --database="${d}" < "${f}"
```

{{< alert "tip" >}}
Импортировать данных можно при помощи конвейера:

```bash
d='DB_NAME'; f="${d}.sql"; xzcat "${f}.xz" | mariadb --user='root' --password --database="${d}"
```
{{< /alert >}}
