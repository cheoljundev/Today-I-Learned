## SUBSTRING_INDEX

```sql
SELECT user_id, email, SUBSTRING_INDEX(email, '@', 1) as id, SUBSTRING_INDEX(email, '@', 2) as domain  from users
```

## SUBSTRING

```sql
SELECT SUBSTRING(created_at, 1, 10) as date, COUNT(*)  from orders
group by date
```