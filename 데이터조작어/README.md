# 데이터 조작어(DML)

### SELECT
* SQL의 SELECT문은 데이터를 검색하는 기본 문장으로 특별히 질의어(query)라고 부른다.

~~~html
SELECT문의 기본 문법
SELECT [ALL | DISTINCT] 속성이름(들)
FROM 테이블이름(들)
[WHERE 검색조건(들)]
[GROUP BY 속성이름]
[HAVING  검색조건(들)]
[ORDER BY 속성이름 [ASC | DESC]]
~~~

~~~html
SELECT bookname, price
FROM Book;
~~~

* 테이블에 있는 Columns 을 검색하고 싶으면 Columns명을 위처럼 적으면 된다. 

~~~html
SELECT *
FROM Book;
~~~

* ' * ' --> 모든 열을 나타냄. 

~~~html
SELECT DISTINCT publisher 
FROM Book;
~~~

* DISTINCT 키워드 : 중복 제거 

* SQL에서 대소문자 구분은 안해도된다. 하지만 예약어는 대문자로 테이블이나 속성이름은 소문자로 적으면 구분하기 쉽다.  

> 세미콜론(;)을 생략해도 되지만 되도록이면 세미콜론을 붙이는 습관을 기르는게 좋다고 한다.
