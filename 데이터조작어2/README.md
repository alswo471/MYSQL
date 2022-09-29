

- 전체 학생의 모든 정보 검색

~~~sql
select * from  학생;
~~~

- 전체 학생의 소속학과 정보를 중복 없이 검색하시오

~~~sql
select distinct 소속학과 from 학생;
~~~

-  통계 학과 , 26살 이상인 학생의 이름과 나이를 검색하시오

~~~sql
select 이름,나이 from 학생 where 나이 >= 26 and 소속학과='통계';
~~~

- 기말성적이 80 이상 90점 이하 내림차순으로 검색

~~~sql
select * 
from 수강
where 기말성적 >= 80 and 기말성적 <= 90
order by 기말성적 desc;
~~~

- 1~3 학년중에서 컴퓨터 학과를 제외한 학생의 이름 학년 소속학과 휴대전화번호를 검색하시오

~~~sql
select 이름, 학년, 소속학과, 휴대전화번호 from 학생 where
(학년>=1 && 학년<=3) or not (소속학과 ='컴퓨터');
~~~

- 위와 동일한 조건으로 다른 문법 사용 

~~~sql
select 이름, 학년, 소속학과, 휴대전화번호 from 학생 
where 학년 between 1 and 3 and not 소속학과='컴퓨터';
~~~

- 컴퓨터 학과나 정보통신과의 학생 이름 학년 소속학과 정보를 학년의 오름차순으로 검색하시오 

~~~sql
select 이름,학년,소속학과 from 학생
where 소속학과='컴퓨터' OR 소속학과='정보통신'
order by 학년 asc;
~~~

- 전체 학생의 정보를 검색하되 학년을 기준으로 먼저 1회차 오름참순 정렬하고 학년이 같은 경우에는 이름을 기준으로 2차 내림차순 정렬하여 검색하시오

~~~sql
select 이름, 학년 from 학생 order by 학년 asc, 이름 desc;
~~~

- 전체 학생수를 검색하시오

~~~sql
select count(*) from 학생 ;
~~~

~~~sql
select count(*)AS 학생수1, count(주소)AS 학생수2, count(distinct 주소)AS 학생수3 from 학생;
~~~

- 2학년 학생수 검색하시오 

~~~sql
select count(*)AS 2학년인원 from 학생 where 학년 = 2; 
~~~

- 여학생의 기말고사 중간고사 성적의 평균값을 구하시오

~~~sql
select avg(중간성적)AS '중간고사평균' , avg(기말성적)AS '기말고사평균'
from 학생 , 수강 where 성별='여';
~~~

- 학생 각 성별의 최고나이와 최저나이를 구하시오

~~~sql
select 성별, max(나이) as 최고나이, min(나이) as 최저나이 from 학생 group by 성별;
~~~

- 각 학년별로 2명 이상의 학생을 갖는 학년에 대해서만 학년별 학생수를 검색하시오.

~~~sql
select 학년, count(*) as '학년별 학생수' from 학생 group by 학년 having count(*)>=2;
~~~

- '이'씨 성을 가진 학생들의 학번과 학생 이름을 검색하시오

~~~sql
select 학번,이름
from 학생
where 이름 like '이__';
~~~
