### GRANT 

* GRANT 문의 형식

~~~
GRANT 권한_내용 ON 권한_대상 TO 사용자_계정;  
GRANT 권한_내용 ON 권한_대상 TO 사용자_계정 with grant option;  
~~~

~~~sql
grant update, select on univdb1.학생21
to 'user41'@'%' with grant option;
~~~

* 사용자 계정의 권한 확인
* 
~~~sql
show grants;
show grants for 'user41'@'%';
~~~

### REVOKE

* REVOKE 문의 형식

~~~
REVOKE 권한_내용 ON 권한_대상 FROM 사용자_계정;
~~~

~~~sql
revoke delete on univdb1.* from 'user41'@'%';
~~~

### DROP USER

* DROP USER 문의 형식

~~~
DROP USER 사용자_계정
~~~

~~~sql
drop user 'user41'@'%';
~~~
