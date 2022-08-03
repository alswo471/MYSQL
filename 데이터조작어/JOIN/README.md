# JOIN

* 주문한 고객

~~~html
SELECT * FROM Customer, Orders 
WHERE Customer.custid = Orders.custid;


~~~

* 주문한 고객중 이름과 가격 

~~~html
SELECT name, saleprice 
FROM Customer, Orders
WHERE Customer.custid = Orders.custid;
~~~

* JOIN 으로 쓰는 방법

~~~html 
SELECT Customer.name, Orders.saleprice
FROM Customer LEFT OUTER JOIN Orders 
ON Customer.custid = Orders.custid;
~~~
