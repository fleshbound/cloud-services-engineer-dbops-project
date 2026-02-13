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
