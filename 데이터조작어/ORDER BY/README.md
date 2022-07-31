# ORDER BY
* SQL 문의 실행 결과 행의 순서는 각 DBMS에 저장된 위치에 따라 결정하므로 실행 결과를 특정 순서대로 출력하고 싶으면 ORDER BY 절을 사용
* 정렬의 기본은 오름차순 , 내림차순으로 정렬하려면 열 이름 다음에 DESC 키워드를 사용

### 도서를 이름순으로 검색 
~~~html
SELECT * 
FROM Book
ORDER BY bookname;
~~~

### 도서를 가격순으로 검색하고, 가격이 같으면 이름순으로 검색

~~~html
SELECT * 
FROM Book
ORDER BY price, bookname;
~~~

### 도서를 가격의 내림차순으로 검색하시오. 만약 가격이 같다면 출판사의 오름차순

~~~html
SELECT * 
FROM Book 
ORDER BY price DESC, publish ASC;
~~~

# GROUP BY

### 집계 함수

* 집계를 하기 위해서는 GROUP BY 문을 사용하고 구체적인 집계 내용은 집계함수를 사용
*최근 버전의 DBMS에서는 다음과 같이 AS를 생략할 수 있다.

* 고객이 주문한 도서의 총 판매액

~~~html
SELECT SUM(saleprice)
FROM Orders;
~~~

* 2번 고객이 주문한 도서의 총 판매액을 구하시오.

~~~html
SELECT SUM(saleprice) AS 총매출
FROM Orders 
WHERE custid=2;
~~~

SQL문에서 GROUP BY절을 사용하면 속성 값이 같은 값끼리 그룹을 만들 수 있다.
HAVING 절은 GROUP BY 절의 결과 나타나는 그룹을 제한하는 역할

*고객별로 주문한 도서의 총 수량과 총 판매액

~~~html
SELECT custid, COUNT(*) AS 도서수량, SUM(saleprice) AS 총액
FROM Orders
GROUP BY custid; 
~~~

>  COUNT 집계함수 : COUNT	SUM([ALL | DISTINCT | *] 속성이름)	COUNT(*)

* 가격이 8,000원 이상인 도서를 구매한 고객에 대해서 고객별 주문 도서의 총 수량을 구하시오. 단 두권 이상 구매한 고객만 구하시오.
* 
~~~html
SELECT SUM(saleprice)
FROM Orders;
~~~

~~~html
SELECT custid, COUNT(*) AS 도서수량
FROM Orders
WHERE saleprice >= 8000
GROUP BY custid 
HAVING COUNT(*) >= 2;
~~~

> HAVING절은 반드시 GROUP BY절과 같이 작성하고 WHERE 절보다 뒤에 나와야 한다. 그리고 <검색조건>에는 SUM, AVG, MAX, MIN, COUNT와 같은 집계함수가 와야 한다.

