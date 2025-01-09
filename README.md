# Домашнее задание к занятию "`Индексы`" - `Солдатенкова Елизавета`

---

### Задание 1

```
SELECT table_schema, sum(index_length / data_length) * 100 "Size in %" FROM information_schema.TABLES GROUP BY table_schema HAVING table_schema = "sakila";```
```

---

### Задание 2

Для оптимизации скрипта были удалены лишние таблицы, добавлен индекс payment_date, изменено условие для использования индекса

```
explain analyze select distinct concat(c.last_name, ' ', c.first_name ), sum(p.amount)
from  payment p inner join customer c on c.customer_id = p.customer_id
where p.payment_date >= '2005-07-30' and p.payment_date < date_add('2005-07-30', INTERVAL 1 DAY) group by p.customer_id;

```

![screenshot](https://github.com/lizaMosiyash/12-05/blob/master/screenshots/Снимок.PNG)
