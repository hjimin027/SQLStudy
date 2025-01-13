출처: w3schools

# 목차
### 기본
1. [기본 syntax](01_Syntax.md) - 핵심 sql 명령들
2. [`SELECT`](02_SELECT.md) - `SELECT`, `SELECT DISTINCT`
3. [특정 조건 - `WHERE`](03_WHERE.md)
4. [정렬](04_ORDER-BY.md) - `ORDER BY`, `ASC`/`DESC`
5. [`AND/OR/NOT`](05_AND_OR_NOT.md) - `WHERE`문에서 사용

### 레코드
6. [새로운 레코드 삽입](06_INSERT-INTO.md) - `INSERT INTO`─`VALUES`
7. [NULL](07_NULL.md) - NULL 확인: `IS NULL`. 비교연산자(=, >, <>) 사용 불가능
8. [레코드 수정](08_UPDATE.md) - `UPDATE`─`SET`
9. [레코드 삭제](09_DELETE.md) - `DELETE FROM`─`WHERE`
10. [반환할 레코드 개수 지정](10_TOP.md) - `TOP`/`LIMIT`/`FETCH FIRST`

### Aggregate Function 집계 함수
11. [Aggregate Functions](11_AggregateFunctions.md)
12. [`MIN()/MAX()`](12_MIN()_MAX().md)
13. [`COUNT()`](13_COUNT().md)
14. [`SUM()`](14_SUM().md)
15. [`AVG()`](15_AVG().md)

### 조건 - `WHERE`문
16. [패턴 찾기](16_LIKE.md) - `LIKE`
17. [Wildcard](17_Wildcard.md) - % _ [] ^ -
18. [범위 내 값 찾기](18_BETWEEN.md) - `BETWEEN`─`AND`
19. [`IN`](19_IN.md) - 여러 `OR`문 축약
20. [Alias](20_Aliases.md) - `AS`

### 집합
21. [Join](21_JOIN.md) - Inner Join, Left Join/Right Join, Full Join, Self Join
22. [두 `SELECT`문 결과집합 결합](22_UNION.md) - `UNION`
23. [`GROUP BY`](23_GROUP-BY.md)

### Subquery
24. [`HAVING`](24_HAVING.md) - `WHERE`대신. Aggregate Function을 조건으로 사용
25. [`EXISTS`](25_EXISTS.md) - 서브쿼리에 레코드가 존재하는지 확인
26. [`ANY`와 `ALL`](26_ANY_ALL.md) - 서브쿼리에 대해 조건을 충족하는 레코드

### 테이블 복사
27. [`SELECT INTO`](27_SELECT-INTO.md) - 한 테이블의 데이터를 다른 테이블로 복사.
28. [`INSERT INTO SELECT`](28_INSERT-INTO-SELECT.md) - 한 테이블의 데이터를 다른 테이블에 삽입(붙여넣기)

### 기타
29. [Case](29_CASE.md) - `CASE`─`WHEN`/`ELSE`─`END`
30. [NULL 처리](30_NULL-Functions.md) - NULL일 경우 다른 값으로 대체. `COALESCE()`, `IFNULL()`, `ISNULL()`, `NVL()`
31. [저장 프로시저](31_Stored-Procedures.md) - `CREATE PROCEDURE`
32. [주석](32_주석.md) - `--`, `/* */`
33. [연산자](33_연산자.md)


* * *

# SQL Intro

## SQL은 무엇인가?
* SQL = Structured Query Language
* 데이터베이스 액세스 및 조작

## SQL은...
SQL은 ANSI/ISO standard이지만, 버전마다 다름

그러나, 최소한의 주요 명령어는 모두 비슷한 방식으로 지원함
> 예: SELECT, UPDATE, DELETE, INSERT, WHERE

## SQL을 웹사이트에 적용하기 위해서는
* RDBMS database program (예: MS Access, SQL Server, MySQL)
* server-side scripting language 사용 (예: PHP, ASP)
* 원하는 데이터를 얻기 위해 SQL 사용
* 페이지를 구성할 HTML/CSS

...이 필요하다.


## RDBMS
RDBMS = Relational Database Management System

RDBMS의 데이터는 Table이라는 데이터베이스 객체에 저장됨

테이블: 관련 데이터 항목의 모음. 행과 열로 구성됨
