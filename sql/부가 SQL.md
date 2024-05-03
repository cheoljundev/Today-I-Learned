## limit

테이블이 클 때 특정 개수만 보기

```sql
SELECT * FROM orders
WHERE payment_method = 'kakaopay'
limit 5
```