## group by

열을 필드로 묶는다.

```sql
SELECT name, count(*) from users
group by name
```

## min, max

최소값, 최대값을 구한다

```sql
SELECT week, min(likes) FROM checkins
group by week
```

```sql
SELECT week, max(likes) FROM checkins
group by week
```

## avg

평균값을 구한다

```sql
SELECT week, avg(likes) FROM checkins
group by week
```

## round

반올림을 한다

```sql
SELECT week, round(avg(likes),2) FROM checkins
group by week
```

## sum

더한다

```sql
SELECT week, sum(likes) FROM checkins
group by week
```

## order by

필드를 정렬

### 오름차순

```sql
SELECT name, count(*) FROM users
group by name
order by count(*)
```

```sql
SELECT * from checkins
order by likes
```

### 내림차순

```sql
SELECT name, count(*) FROM users
group by name
order by count(*) DESC
```

```sql
SELECT * from checkins
order by likes DESC
```