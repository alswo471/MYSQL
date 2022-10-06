### LIKE 문자 연산자 검색

- 주소가 과천으로 끝나는 학생을 출력

~~~sql
select * from 학생 where 주소 like binary '%과천';
~~~

- 소속학과가 컴퓨터로 끝나고 주소가 분당으로 끝나는 학생을 출력

~~~sql
select * from 학생 where 소속학과 like binary '%컴퓨터' and 주소 like binary '%분당';
~~~

### 널값검색: IS NULL, IS NOT NULL

- 휴대전화번호가 null 인 학생의 이름만 출력

~~~sql
select 이름 from 학생 where 휴대전화번호 is null;
~~~

~~~sql
select 이름 from 학생 where 휴대전화번호 is not null;
~~~

### 집합연산자를이용한검색: UNION

- 성별이 '여' 이고 평가학점이 A 인 학생의 학번만 출력

~~~sql
select 학번 from 학생 where 성별='여' 
union 
select 학번 from 수강 where 평가학점='A';
~~~


- 남학생이거나 과목번호 'c002' 인 학생의 학번만 출력

~~~sql
select 학번 from 학생 where 성별='남' 
union 
select 학번 from 수강 where 과목번호='c002';
~~~

### 부질의문을 이용한 검색

- 학생테이블에서 소속학과가 통계 와 정보통신 인 학생을 출력 

~~~sql
select * from 학생 where 소속학과 in('통계', '정보통신');
~~~

- 평가학점이 A , B 인 학번만 출력 

~~~sql
select 학번 from 수강 where 평가학점 in('A', 'B');
~~~

- 수강테이블에서 평가학점이 A,B 인 학생수를 별칭을 'A/B 학점 학생수' 으로 출력

~~~sql
select count(*)AS 'A/B 학점 학생수' from 수강 where 평가학점 in('A','B');
~~~

- 부 질의문  과목번호가 'c002' 인 과목을 수강한 학생의 이름을 검색 

~~~sql
select 학번 from 수강 where
과목번호 =(
select 과목번호 from 과목 where 이름='정보보호');
~~~

- 중첩 부 질의문 '정보보호' 과목을 수강한 학생의 이름을 검색

~~~sql
select 이름 from 학생 where 학번 in
(select 학번 from 수강 where
과목번호 =(
select 과목번호 from 과목 where 이름='정보보호'));
~~~

- exists 연산자

~~~sql
select 이름 from 학생 where exists( 
select * from 수강 where 수강.학번=학생.학번 and 과목번호='c002');
~~~

- 수강테이블에서 수강의 학번과 학생의 학번이 같은 데이터를 모두 검색

~~~sql
select 이름 from 학생 where exists( SELECT * FROM 수강 WHERE 수강.학번=학생.학번);
~~~

- 응용) 학생테이에서 학생 중에서 한과목도 수강하지 않은 학생의 이름을 출력

~~~sql
SELECT 이름 FROM 학생 WHERE 
  NOT EXISTS(SELECT * FROM 수강 WHERE 수강.학번=학생.학번);
~~~

### JOIN

#### 크로스조인(cross join)
  
~~~sql
select count(*) from 학생,수강;
~~~

~~~sql
select count(*) from 학생 cross join 수강;
~~~ 
  
~~~sql
select count(*) from 학생, 수강
where 학생.학번=수강.학번;
~~~

#### 동등조인(equijoin)

- 전체 학생의 기본 정보와 모든 수강 정보를 검색

~~~sql
select * from 학생,수강 where 학생.학번=수강.학번;
~~~

~~~sql
select * from 학생 join 수강 on 학생.학번=수강.학번;
~~~

