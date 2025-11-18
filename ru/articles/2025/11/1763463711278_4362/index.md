---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'PostgreSQL: Роли'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'postgresql'
tags:
  - 'postgresql'
  - 'user'
  - 'role'
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

date: '2025-11-18T14:01:51+03:00'
publishDate: '2025-11-18T14:01:51+03:00'
lastMod: '2025-11-18T14:01:51+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: 'e99a7df9ee74226131fbd228415f1ef00001450e'
uuid: 'e99a7df9-ee74-5261-a1fb-d228415f1ef0'
slug: 'e99a7df9-ee74-5261-a1fb-d228415f1ef0'

draft: 0
---

Работа с ролями (пользователями) в {{< tag "PostgreSQL" >}}.

<!--more-->

- Посмотреть список ролей:

```bash
sudo -u 'postgres' psql -c '\du'
```

- Создать роль `DB_USER` с паролем:

```bash
sudo -u 'postgres' createuser --pwprompt 'DB_USER'
```

- Переименовать роль `DB_USER` в `DB_USER_NEW`:

```bash
sudo -u 'postgres' psql -c 'alter role DB_USER rename to DB_USER_NEW;'
```

- Сделать роль `DB_USER` супер-пользователем:

```bash
sudo -u 'postgres' psql -c 'alter role DB_USER superuser;'
```

- Изменить пароль у роли `DB_USER`:

```bash
sudo -u 'postgres' psql -c "alter role DB_USER with password 'PASSWORD';"
```

- Удалить пароль у роли `DB_USER`:

```bash
sudo -u 'postgres' psql -c 'alter role DB_USER with password null;'
```

- Удалить роль `DB_USER`:

```bash
sudo -u 'postgres' dropuser 'DB_USER'
```

- Изменить роль владельца у всех баз данных с `DB_USER` на `DB_USER_NEW`:

```bash
sudo -u 'postgres' psql -c 'reassign owned by DB_USER to DB_USER_NEW;'
```

- Изменить роль у таблиц базы данных `DB_NAME` с `DB_USER` на `DB_USER_NEW`:

```bash
sudo -u 'postgres' psql -c '\c DB_NAME' -c 'reassign owned by DB_USER to DB_USER_NEW;'
```
