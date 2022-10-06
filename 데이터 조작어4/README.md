### UPDATE문

- 학번이 g002 인 학생의 주소를 '경기 성남' 으로 수정하시오

~~~sql
update 학생1 set 주소 = '경기 성남' where 학번 ='g002';
~~~

- 학번이 g001 인 학생의 소속학과를 '경영' 으로 수정하시오

~~~sql
update 학생1 set 소속학과 = '경영' where 학번 ='g001';
~~~

- 학번이 'g002'인 학생의 소속학과를 '빅테이터'로 수정하시오

~~~sql
update 학생1 set 소속학과 = '빅데이터' where 학번 ='g002';
~~~

- 수강1 테이블의 중간성적을 모두 +5 증가 시키시오

~~~sql
update 수강1 set 중간성적=중간성적+5;
~~~

- 수강 내용이 없는 학생의 소속학과를 널 값으로 수정하시오.

~~~sql
update 학생1 set 소속학과 = null 
where 학번 not in(select 학번 from 수강1);
~~~

- 학번이 s003 인 학생의 수강 내용을 '이은진' 학생이 수강한 것으로 수정하시오

~~~sql
update 수강1 set 학번=
(select 학번 from 학생1 
where 이름='이은진')
where 학번='s003';
~~~

### DELECT 문

- '송윤아' 학생의 모든 정보를 삭제

~~~sql
delete from 학생1 where 이름='송윤아';
~~~

- 수강자가 2명 미만인 과목에 대한 정보를 모두 삭제

~~~sql
delete from 과목1 where 과목번호 in(select 과목번호 
from 수강1 
group by 과목번호 
having count(*)<2);
~~~
