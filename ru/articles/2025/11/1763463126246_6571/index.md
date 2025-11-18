---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'MariaDB: Базы данных'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'mariadb'
tags:
  - 'mariadb'
  - 'database'
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

date: '2025-11-18T13:52:08+03:00'
publishDate: '2025-11-18T13:52:08+03:00'
lastMod: '2025-11-18T13:52:08+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: 'c3432f1c5c2888e9675dd6ee06564a6c611c8861'
uuid: 'c3432f1c-5c28-58e9-975d-d6ee06564a6c'
slug: 'c3432f1c-5c28-58e9-975d-d6ee06564a6c'

draft: 0
---

Работа с базами данных в {{< tag "MariaDB" >}}.

<!--more-->

- Посмотреть список баз данных:

```bash
echo 'show databases;' | mariadb --user='root' --password
```

- Посмотреть список таблиц в базе данных `DB_NAME`:

```bash
echo 'show full tables from DB_NAME;' | mariadb --user='root' --password
```

- Создать базу данных `DB_NAME` с кодировкой `utf8mb4` и сопоставлением `utf8mb4_unicode_ci`:

```bash
echo "create database if not exists DB_NAME character set 'utf8mb4' collate 'utf8mb4_unicode_ci';" | mariadb --user='root' --password
```

- Изменить кодировку и сопоставление базы данных на `utf8mb4` и `utf8mb4_unicode_ci` соответственно:

```bash
echo "alter database DB_NAME character set 'utf8mb4' collate 'utf8mb4_unicode_ci';" | mariadb --user='root' --password
```

- Удалить базу данных `DB_NAME`:

```bash
echo 'drop database if exists DB_NAME;' | mariadb --user='root' --password
```
