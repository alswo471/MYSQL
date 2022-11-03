## 사용자 정의 함수 (user defined

- 사용자가 직접 정의한 함수로 DBMS 안에 독립된 데이터베이스 객체로 저장

- SELECT 문이나 프로시저 안에서 호출되어 특정 기능을 수행하고 결과 값을 반환하는 용
도로 사용

- 스칼라 함수는 하나의 값 또는 NULL 을 반환

- 테이블 함수는 각 행이 하나 이상의 열로 구성된 테이블을 반환

<br/>

- 사용자 정의 함수를 생성하는 CREATE FUNCTION 명령문의 형식

~~~sql
CREATE FUNCTION 함수명(매개변수 매개변수_자료형)
RETURNS 반환값_자료형
BEGIN
...
SQL 명령문 ;
...
RETURNS 반환값 ;

END 
~~~

<br/>

~~~sql
DELIMITER // 
CREATE FUNCTION Fn_Grade(grade CHAR(1))
RETURNS VARCHAR(10)
BEGIN
DECLARE ret_grade VARCHAR(10);
IF(grade = 'A') THEN
	SET ret_grade = '최우수';
ELSEIF(grade = 'B') THEN
	SET ret_grade = '우수' ;
ELSEIF(grade = 'ㅊ') THEN
	SET ret_grade = '보통' ;
ELSEIF(grade = 'D' OR grade = 'F') THEN
	SET ret_grade = '미흡' ;
END IF ; 
RETURN ret_grade ;
END 
//
~~~

<br/>

> 만약 오류 코드: 1418 가 발생하면 아래 코드 쿼리 날려준 후 실행

<br/>

~~~sql 
SET GLOBAL log_bin_trust_function_creators = 1;
~~~

<br/>

- 결과

~~~sql
SELECT 학번, 과목번호, 평가학점, Fn_Grade(평가학점)AS '평가 등급' FROM 수강;
~~~

<img width="196" alt="image" src="https://user-images.githubusercontent.com/92145785/199668649-56049dc9-46c1-43d7-875d-17bba21f4b05.png">
