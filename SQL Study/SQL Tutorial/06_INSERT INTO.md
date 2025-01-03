# INSERT INTO
테이블에 새로운 레코드를 삽입하는 데 사용

## 두 가지 방법으로 사용할 수 있다..
1. 삽입할 열의 이름과 값을 모두 지정 - 지정되지 않은 열은 null
   ```sql
   INSERT INTO table_name (col1, col2, col3, ...)
   VALUES (value1, value2, value3, ...);
   ```
2. 테이블의 모든 열에 대한 값을 지정 → 열 이름을 지정할 필요X. 순서가 맞는지 확인해야 함
   ```sql
   INSERT INTO table_name
   VALUES (value1, value2, value3, ...);
   ```

## 여러 행 삽입
```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES
('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway'),
('Greasy Burger', 'Per Olsen', 'Gateveien 15', 'Sandnes', '4306', 'Norway'),
('Tasty Tee', 'Finn Egan', 'Streetroad 19B', 'Liverpool', 'L1 0AA', 'UK');
```
각 값은 쉼표로 구분
