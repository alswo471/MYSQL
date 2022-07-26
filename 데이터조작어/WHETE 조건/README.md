## WHERE 조건

* WHERE절은 조건에 맞는 검색에 사용

### 비교

~~~html
SELECT * 
FROM Book 
WHERE bookid < 5;
~~~

* = , <> , <= , > , >= 등 사용


### 범위 
 
~~~html
SELECT * 
FROM Book 
WHERE bookid BETWEEN 5 AND 10;
~~~

* BETWEEN 연사자는 값의 범위를 지정(논리 연산자인 AND를 같이 사용 가능)
 
### 집합 

~~~html
SELECT * 
FROM Book 
WHERE publisher IN ('삼성당', '한솔의학서적');
~~~

~~~html
SELECT * 
FROM Book 
WHERE publisher NOT IN ('삼성당', '한솔의학서적');
~~~

* IN : 집합의 원소인지 판단 
* NOT IN : 선택한 집합의 원소가 아닌 것들을 검색(삼성당, 한솔의학서적이 아닌 출판사 검색)

### 패턴

~~~html
SELECT bookname, publisher 
FROM Book
 WHERE bookname LIKE '축구아는 여자';
~~~

~~~html
SELECT bookname, publisher
FROM Book
WHERE bookname LIKE '%축구%';
~~~

~~~html
SELECT bookname, publisher
FROM Book
WHERE bookname LIKE '축구%';
~~~

~~~html
SELECT * 
FROM Book
WHERE bookname LIKE '_구%';
~~~

* %축구%' : 축구를 포함하는 문자열

* %축구 : 키워드로 끝나는 팬턴

* 축구% : 키워드로 시작하는 패턴

* '_구%' : 두 번째 위치에 '구'가 들어가는 문자열( _ _  언더바 두개쓰면 3번째 위치)

* '+' : 문자열을 연결
* [] : 1개의 문자와 일치
* [^]	: 1개의 문자와 불일치
