## SHOW

테이블을 보여준다

```sql
SHOW TABLES
```

## SELCET

데이터를 가져온다.

```sql
SELECT * FROM TABLE1
```

```sql
SELECT field1, field2 FROM TABLE1
```

## WHERE

정확히 어떤 데이터를 가져올지 설정

- payment_method필드의 값이 kakaopay인 행만


```sql
SELECT * FROM orders
WHERE payment_method = 'kakaopay' 
```

- 값 비교도 가능

```sql
SELECT * FROM point_users
WHERE point > 5000
```

- and, or도 가능

```sql
SELECT * FROM orders
WHERE course_title = '앱개발 종합반' and payment_method = 'CARD'
```

```sql
SELECT * FROM orders
WHERE course_title = '앱개발 종합반' or payment_method = 'CARD'
```

- 같지 않음

```sql
SELECT * FROM orders
WHERE course_title != '웹개발 종합반'
```

- 사이에 있는 값 가져오기

```sql
SELECT * FROM orders
WHERE created_at BETWEEN '2020-07-13' and '2020-07-15'
```

- 안에 있는 값 가져오기

```sql
SELECT * FROM checkins
WHERE week in(1,3)
```

- 문자열 부분일치 검색 (패턴)

```sql
SELECT * FROM users
WHERE email LIKE '%daum.net'
```

```sql
SELECT * FROM users
WHERE email LIKE 'a%t'
```

