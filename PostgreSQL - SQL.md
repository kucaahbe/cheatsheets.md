JSON field is empty:

```sql
SELECT id, delivery FROM service_requests WHERE delivery::text <> '{}';
```

JSON subfield is NULL:

```sql
SELECT id, extra FROM contents WHERE (extra->>'schedule_time_block') IS NULL LIMIT 5
```