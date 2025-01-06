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
select distinct  concat(c.last_name, ' ', c.first_name ), sum(p.amount) over (partition by c.customer_id )
from payment p, rental r, customer c
where p.payment_date >= '2005-07-30 00:00:00' AND p.payment_date < '2005-07-30 23:59:59'  and p.payment_date = r.rental_date and r.customer_id = c.customer_id

```

