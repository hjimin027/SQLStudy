# NULL Functions

###### SQL 종류마다 다름..

Products 테이블이 다음과 같다고 하자.
|P_Id|ProductName|UnitPrice|UnitsInStock|UnitsOnOrder|
|----|-----------|---------|------------|------------|
|1|Jarlsberg|10.45|16|15|
|2|Mascarpone|32.56|23||
|3|Gorgonzola|15.67|9|20|

UnitsOnOrder열에 NULL 값이 존재한다. 그럼,
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + UnitsOnOrder)
FROM Products;
```
위의 코드에서, UnitsOnOrder 값이 NULL이면, 결과가 NULL이 된다.

이를 해결하기 위해 다음 방법이 있다.

## IFNULL(), ISNULL(), COALESCE(), NVL()
###### coalesce: 병합하다, 합체하다. 두 열을 병합하는 것을 이용해 NULL을 특정 값으로 변환
NULL값을 대체할 값 지정

* MySQL: IFNULL(), COALESCE()
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products;
```
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))
FROM Products;
```

* SQL Server: ISNULL(), COALESCE()
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + ISNULL(UnitsOnOrder, 0))
FROM Products;
```

* MS Access: IsNull()
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + IsNull(UnitsOnOrder, 0))
FROM Products;
```

* Oracle: NVL(), COALESCE()
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + NVL(UnitsOnOrder, 0))
FROM Products;
```
