### 1. 숫자 함수

~~~sql
select abs(+17), abs(-17), ceil(3.28), floor(4.259);
~~~


~~~sql
select * from 수강;
select 학번, sum(기말성적)/count(*),round(sum(기말성적)/count(*),1)
from 수강
group by 학번;
~~~

<br/>

### 2. 문자 함수

~~~sql
select length(소속학과), right(학번,2), repeat('*',나이), concat(소속학과,'학과')
from 학생;
~~~

~~~sql
select substring(주소,1,2), replace(substring(휴대전화번호,5,9),'-',',')
from 학생;
~~~

<br/>

### 3. 날짜/시간 함수

~~~sql
select 신청날.last_day(신청날짜)
from 수강
where year(신청날자) ='2019';
~~~
