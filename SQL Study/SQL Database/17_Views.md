# View란?
View: 하나 이상의 기본 테이블이나 다른 뷰를 이용해 생성되는 가상 테이블  
sql문의 결과 집합을 가상 테이블로 이용

뷰는 실제 테이블처럼 행과 열을 포함함. 뷰의 필드는 DB에 있는 실제 테이블의 필드 중 하나 이상

View에 sql문과 함수를 추가하여, 데이터가 단일 테이블에서 오는 것처럼 표시할 수 있음

#### [뷰 추가 설명](https://reeme.tistory.com/54)
뷰의 개념
* 기본 테이블은 디스크에 공간이 할당되어 데이터를 저장하지만, 뷰는 디스크 저장 공간이 할당되지 않는다.
* 뷰는 데이터 딕셔너리(Data Dictionary) 테이블에 SQL문(뷰에 대한 정의)만 저장된다.
* 뷰에 대한 수정 결과는 뷰를 정의한 기본 테이블에 적용된다.
* 뷰를 정의한 기본 테이블에서 정의된 무결성 제약조건(Integrity Constraint)은 그대로 유지된다.

뷰의 필요성
* 사용자마다 특정 객체만 조회할 수 있도록 할 필요가 있음(모든 직원에 대한 정보를 모든 사원이 볼 수 있도록 하면 안됨)
* 복잡한 쿼리문 단순화 가능
* 데이터 중복성 최소화
  - 판매부에 속한 사원들만 사원 테이블에서 찾아서 다른 테이블로 만들면 중복성 발생 → 뷰 필요
# View 생성
`CREATE VIEW` 사용
## 뷰 생성 Syntax
```sql
CREATE VIEW view_name AS
SELECT col1, col2, ...
FROM table_name
WHERE condition;
```
참고: 뷰는 항상 최신 데이터를 표시!! 사용자가 뷰를 쿼리할 때마다, 데이터베이스는 뷰를 재생성한다.

#### 예시
```SQL
-- Brazil의 모든 customers를 보여주는 view 생성 --
CREATE VIEW [Brazil Customers] AS
SELECT CustomerName, ContactName
FROM Customers
WHERE Country = 'Brazil';
```
위의 뷰를 다음과 같이 쿼리할 수 있다.
```sql
SELECT * FROM [Brazil Customers];
```

<br>

다른 예시를 들어보자.
```sql
-- 가격이 평균 가격보다 높은 모든 product을 보여주는 view 생성 --
CREATE VIEW [Products Above Average Price] AS
SELECT ProductName, Price
FROM Products
WHERE Price > (SELECT AVG(Price) FROM Products);
```
위의 뷰는 다음과 같이 쿼리할 수 있다.
```sql
SELECT * FROM [Products Above Average Price];
```

# View 업데이트
`CREATE OR REPLACE VIEW` 사용
## 뷰 업데이트 Syntax
```SQL
CREATE OR REPLACE VIEW view_name AS
SELECT col1, col2, ...
FROM table_name
WHERE condition;
```
#### 예시
```sql
-- [Brazil Customers]뷰에 City 열 추가 --
CREATE OR REPLACE VIEW [Brazil Customers] AS
SELECT Customername, ContactName, City
FROM Customers
WHERE Country = 'Brazil';
```

 # View 삭제
 `DROP VIEW` 사용
 ## Syntax
 ```SQL
DROP VIEW view_name;
```
#### 예시
```sql
DROP VIEW [Brazil Customers];
```
