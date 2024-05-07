## limit

테이블이 클 때 특정 개수만 보기

```sql
SELECT * FROM orders
WHERE payment_method = 'kakaopay'
limit 5
```

## distinct

중복 제거하고 보기

```sql
SELECT distinct(payment_method) FROM orders
```

## count

개수 세기

```sql
SELECT count(*) FROM orders
```

```sql
SELECT count(*) FROM orders
WHERE payment_method = 'kakaopay'
```

### distinct count 결합

```sql
SELECT count(distinct(name)) FROM users
```

## alias

```sql
SELECT * FROM orders o
WHERE o.course_title = '앱개발 종합반'
```

```sql
SELECT payment_method, COUNT(*) as cnt  FROM orders o
WHERE o.course_title = '앱개발 종합반'
GROUP BY payment_method 
```