데이터 정의어 명령은 ROLLBACK이 불가능하다.

## CREATE

테이블을 생성

```sql
CREATE TABLE EMP_DDL(
 	EMPNO	 NUMBER(4),
 	ENAME	 VARCHAR2(10),
 	JOB		 VARCHAR2(9),
 	MGR		 NUMBER(4),
 	HIREDATE DATE,
 	SAL 	 NUMBER(7,2),
 	COMM 	 NUMBER(7,2),
 	-- 총 7자리, 소수점 2자리
 	DEPTNO	 NUMBER(2)
)
```

## ALTER

이미 생성된 데이터베이스 객체를 변경

### ADD

기존 테이블에 열 추가

```sql
ALTER TABLE EMP_ALTER
  ADD HP VARCHAR2(20);
```

### RENAME

열 이름을 변경

```sql
ALTER TABLE EMP_ALTER
  RENAME COLUMN HP TO TEL
```

### MODIFY

열의 자료형 변경

```sql
ALTER TABLE EMP_ALTER 
MODIFY EMPNO NUMBER(5)
```

### DROP

열을 삭제

```sql
ALTER TABLE EMP_ALTER
DROP COLUMN TEL
```

## RENAME

테이블의 이름을 변경

```sql
RENAME EMP_ALTER TO EMP_RENAME
```

## TRUNCATE

테이블의 모든 데이터를 삭제

```sql
TRUNCATE TABLE EMP_RENAME
```

## DROP

테이블을 삭제

```sql
DROP TABLE EMP_RENAME
```