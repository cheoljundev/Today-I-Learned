## 기본 case

```sql
SELECT pu.user_id, pu.point,
       (case when pu.point > 10000 then '잘 하고 있어요'
       else '조금만 더 파이팅' END) as msg
  from point_users pu 
```
## 통계 내기

```sql
SELECT pu.user_id, pu.point,
       (case when pu.point > 10000 then '1만 이상'
             when pu.point > 5000 then '5천 이상'
             else '5천 미만' END) as lv
  from point_users pu 
```

```sql
SELECT a.lv, COUNT(*) as cnt  from (
	SELECT pu.user_id, pu.point,
	       (case when pu.point > 10000 then '1만 이상'
	             when pu.point > 5000 then '5천 이상'
	             else '5천 미만' END) as lv
	  from point_users pu
) a
group by a.lv
```

```sql
with table1 as (
	SELECT pu.user_id, pu.point,
	       (case when pu.point > 10000 then '1만 이상'
	             when pu.point > 5000 then '5천 이상'
	             else '5천 미만' END) as lv
	  from point_users pu
)

SELECT a.lv, COUNT(*) as cnt  from table1 a
group by a.lv
```