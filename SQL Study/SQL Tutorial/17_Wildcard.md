# Wildcard

String에서, 하나 이상의 문자를 대체하는 데 사용

`WHERE`문 안에서, `LIKE`와 함께 사용

## Wildcard Characters

|기호|설명|
|-|-|
|%|0개 이상의 글자|
|_|한 글자|
|[]|괄호[] 안의 글자 중 하나|
|^|[] 안에서 사용. 괄호 안의 글자들을 제외한 글자 중 하나|
|-|[] 안에서 사용. 범위를 지정하는 역할|
|{}|이스케이프 문자(예.\n) 중 아무거나. Oracle에서만 지원|

## 예시
#### %, _
[여기](16_LIKE.md)에서 확인

#### []
괄호[] 안의 글자 중 하나
```sql
-- 'b'나 's', 'p'로 시작하는 모든 customer 반환 --
SELECT * FROM Customers
WHERE CustomerName LIKE '[bsp]%';
```

#### -
괄호[] 안에서 범위 지정
```sql
-- 'a', 'b', 'c', 'd', 'e', 'f' 중 하나로 시작하는 모든 customer 반환 --
SELECT * FROM Customers
WHERE CustomerName LIKE '[a-f]%';
```


## (+) 보충
### 괄호[] 와일드카드 부정
1. NOT 사용
   ```sql
   SELECT * FROM Customers
   WHERE NOT CustomerName LIKE '[bsp]%';
   ```
2. ^(캐럿 문자) 사용

   ^: 캐럿문자, 삿갓표. 대괄호 안에 들어갈 경우, 대괄호 안의 문자가 아닌 다른 것만 출력하라는 의미.
   ```sql
   SELECT * FROM Customers
   WHERE CustomerName LIKE '[^bsp]%';
   ```
