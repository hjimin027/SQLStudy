# NULL Values

## NULL값 이란?
값이 존재하지 않는 필드.

## NULL 확인
`IS NULL`이나 `IS NOT NULL`을 사용해야 함.

null값은 비교연산자(=, <, <>) 사용 불가능

## Syntax
#### IS NULL
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```
#### IS NOT NULL
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```
