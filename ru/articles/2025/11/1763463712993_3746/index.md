---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'PostgreSQL: Базы данных'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'postgresql'
tags:
  - 'postgresql'
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

date: '2025-11-18T14:01:53+03:00'
publishDate: '2025-11-18T14:01:53+03:00'
lastMod: '2025-11-18T14:01:53+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: 'f734f9e519df881c8c1cd5f6b9deef192d9b3464'
uuid: 'f734f9e5-19df-581c-8c1c-d5f6b9deef19'
slug: 'f734f9e5-19df-581c-8c1c-d5f6b9deef19'

draft: 0
---

Работа с базами данных в {{< tag "PostgreSQL" >}}.

<!--more-->

- Посмотреть список баз данных:

```bash
sudo -u 'postgres' psql -c '\l'
```

- Посмотреть список таблиц схемы `public` в базе данных `DB_NAME`:

```bash
sudo -u 'postgres' psql -c '\c DB_NAME' -c '\dt'
```

- Посмотреть список таблиц всех схем в базе данных `DB_NAME`:

```bash
sudo -u 'postgres' psql -c '\c DB_NAME' -c '\dt *.*'
```

- Создать базу данных `DB_NAME` с владельцем `DB_USER` при помощи утилиты `createdb`:

```bash
sudo -u 'postgres' createdb --owner='DB_USER' --locale-provider='builtin' --builtin-locale='C.UTF-8' --encoding='UTF8' 'DB_NAME'
```

- Создать базу данных `DB_NAME` с владельцем `DB_USER` при помощи SQL-команды:

```sql
create database 'DB_NAME' owner 'DB_USER' locale_provider 'builtin' builtin_locale 'C.UTF-8' encoding 'UTF8';
```

- Создать базу данных `DB_NAME` из шаблона `template0` с владельцем `DB_USER` при помощи утилиты `createdb`:

```bash
sudo -u 'postgres' createdb --owner='DB_USER' --locale-provider='builtin' --builtin-locale='C.UTF-8' --encoding='UTF8' --template='template0' 'DB_NAME'
```

- Создать базу данных `DB_NAME` из шаблона `template0` с владельцем `DB_USER` при помощи SQL-команды:

```sql
create database 'DB_NAME' owner 'DB_USER' locale_provider 'builtin' builtin_locale 'C.UTF-8' encoding 'UTF8' template 'template0';
```

- Удалить базу данных `DB_NAME` при помощи утилиты `dropdb`:

```bash
sudo -u 'postgres' dropdb --if-exists 'DB_NAME'
```

- Удалить базу данных `DB_NAME` при помощи SQL-команды:

```sql
drop database if exists 'your_database_name';
```
