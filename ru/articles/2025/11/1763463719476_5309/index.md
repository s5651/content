---
# -------------------------------------------------------------------------------------------------------------------- #
# GENERAL
# -------------------------------------------------------------------------------------------------------------------- #

title: 'PostgreSQL: Обновление кластера'
description: ''
icon: 'far fa-file-lines'
categories:
  - 'postgresql'
tags:
  - 'postgresql'
  - 'cluster'
  - 'upgrade'
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

date: '2025-11-18T14:02:00+03:00'
publishDate: '2025-11-18T14:02:00+03:00'
lastMod: '2025-11-18T14:02:00+03:00'

# -------------------------------------------------------------------------------------------------------------------- #
# META
# -------------------------------------------------------------------------------------------------------------------- #

type: 'articles'
hash: 'f2e49d9d5891b97928743a4144d4dc655a36a1ac'
uuid: 'f2e49d9d-5891-5979-9874-3a4144d4dc65'
slug: 'f2e49d9d-5891-5979-9874-3a4144d4dc65'

draft: 0
---

Обновление кластера {{< tag "PostgreSQL" >}}.

<!--more-->

{{< alert "important" >}}
В данном примере рассматривается сценарий обновления PostgreSQL **16** до PostgreSQL **17** на ОС **Debian**.
{{< /alert >}}

- Посмотреть список экземпляров PostgreSQL в кластере:

```bash
pg_lsclusters
```

- Установить новую версию PostgreSQL 17:

```bash
apt install postgresql-17
```

{{< accordion-item "TimescaleDB" >}}
- Установить новую версию TimescaleDB для PostgreSQL 17:

```bash
apt install timescaledb-2-postgresql-17 timescaledb-2-loader-postgresql-17
```

- Импортировать настройки TimescaleDB в конфигурацию PostgreSQL 17:

```bash
timescaledb-tune --quiet --yes && systemctl restart postgresql@17-main.service
```
{{< /accordion-item >}}

- Остановить новую версию экземпляра PostgreSQL 17 в кластере:

```bash
pg_dropcluster --stop 17 main
```

- Запустить обновление версии экземпляра PostgreSQL 16 до PostgreSQL 17 в кластере:

```bash
pg_upgradecluster 16 main
```

- Удалить версию экземпляра PostgreSQL 16 из кластера:

```bash
pg_dropcluster 16 main
```

- Посмотреть установленные пакеты для PostgreSQL 16 и удалить ненужные:

```bash
apt list --installed | grep 'postgresql.*-16'
```
