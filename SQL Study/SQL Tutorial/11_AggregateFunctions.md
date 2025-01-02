# Aggregate Function 집계 함수
(집합 관련됨. aggregate이 집합 말하는거임)

집합에 대한 연산을 수행하고, 단일 값을 반환

종종 `SELECT`문의 `GROUP BY`절과 함께 사용됨

#### 자주 사용되는 SQL aggregate function
* `MIN()` : 선택된 열에서 가장 작은 값 반환
* `MAX()` : 선택된 열에서 가장 큰 값 반환
* `COUNT()` : 집합의 행 수 반환
* `SUM()` : 숫자형 열의 총 합 반환
* `AVG()` : 숫자형 열의 평균 반환

**Aggregate function은 null값을 무시한다. `COUNT()` 제외하고!!**
