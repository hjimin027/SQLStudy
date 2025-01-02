# DELETE
테이블에 존재하는 레코드를 삭제할 때 사용

## Syntax
```sql
DELETE FROM table_name WHERE condition;
```
#### 주의점
`WHERE`를 반드시 지정행 함!! 지정 안 하면 테이블의 모든 레코드가 삭제됨

## 예시
#### 삭제
```sql
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```
#### 모든 레코드 삭제
테이블은 삭제하지 않음!! 테이블의 구조, 특성, 인덱스는 유지됨
```sql
DELETE FROM table_name;
```

#### 테이블 삭제
테이블을 완전히 삭제
```sql
DROP TABLE Customers;
```
