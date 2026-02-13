# dbops-project
Исходный репозиторий для выполнения проекта дисциплины "DBOps"

## Описание DDL-запросов
Создание БД `store`:

```sql
CREATE DATABASE store;
```

Создание пользователя для выполнения миграций и автотестов:

```sql
CREATE USER service WITH PASSWORD '';
```

Выдача прав на схему `public`:

```sql
GRANT USAGE ON SCHEMA public TO service;
GRANT CREATE ON SCHEMA public TO service;
```

Выдача прав на таблицы в схеме `public`:

```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO service;
```

Запрос, позволяющий определить количество сосисок, проданных за каждый день предыдущей недели:

```sql
SELECT o.date_created, SUM(op.quantity) as amount
FROM orders o
JOIN order_product op ON o.id = op.order_id
WHERE o.status = 'shipped' AND o.date_created > NOW() - INTERVAL '1 WEEK'
GROUP BY o.date_created
ORDER BY o.date_created desc;
```

Время выполнения запроса
- без индексов: 25,660 мс
