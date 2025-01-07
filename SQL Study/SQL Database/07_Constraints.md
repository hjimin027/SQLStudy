# Constraints
테이블의 데이터에 규칙을 지정하기 위해 사용

## Constraints 생성
`CREATE TABLE`로 테이블이 생성될 때 지정. 혹은 `ALTER TABLE`로 수정할 때 지정

## Syntax
```sql
CREATE TABLE table_name (
    col1 datatype constraint,
    col2 datatype constraint,
    ...
);
```

## SQL Constraints
Constraints(이하 제약조건)은 테이블의 데이터에 규칙을 지정하는 데 사용된다.

제약조건은 테이블에 들어갈 수 있는 데이터의 타입을 제한한다. 이를 통해 테이블의 정확성과 신뢰성을 보장한다.

제약조건은 열 수준 혹은 테이블 수준일 수 있다.

다음은 일반적으로 사용되는 Constraint이다:
* `NOT NULL`: 열에 NULL값이 들어올 수 없다.
* `UNIQUE`: 해당 열의 모든 값이 고유값이어야 한다.
* `PRIMARY KEY`: `NOT NULL`과 `UNIQUE`의 결합. 각 행을 고유하게 식별한다.
* `FOREIGN KEY`: 테이블 간 링크를 파괴하는 것을 방지한다.
* `CHECK`: 열의 값이 특정 조건을 만족하는지 확인한다.
* `DEFAULT`: 값이 지정되지 않은 경우 기본값을 설정한다.
* `CREATE INDEX`: 인덱스 생성. 데이터베이스에서 데이터를 빠르게 생성하고 검색할 때 사용한다.
