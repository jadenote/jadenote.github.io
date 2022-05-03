# SQL_HackerRank_Advanced Select_New Companies

![image](https://user-images.githubusercontent.com/99947811/166395535-77843e3c-2d10-4b3b-84a3-5035559601b6.png)

### Problem
Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

Link(https://www.hackerrank.com/challenges/the-company/problem?isFullScreen=true)

* Distinct 는 한번만 쓸 수 있다
    - SELECT DISTINCT (E.manager_code), Distinct (C.founder) (X)
    - SELECT DISTINCT (E.manager_code, C.founder)  (X)
    - SELECT DISTINCT E.manager_code,  C.founder (O)


```python
# 1. 중복값들을 제거하여 한 테이블로 모은다
SELECT E.employee_code, E.manager_code, E.senior_manager_code, E.lead_manager_code, C.founder
FROM (SELECT DISTINCT * FROM Employee) AS E
    LEFT JOIN (SELECT DISTINCT * FROM Company) AS C
    ON E.company_code = C.company_code


```

### Solution(해답)

* FROM + 뒤에 여러 개의 테이블과 alias를 넣을 수 있다!
* 문제 카테고리가 Advanced Select이다. INNER JOIN 외에 다른 방법으로 풀 수 있다!!
* 근데 run code누르고 결과값 나오기까지 약 30초 걸렸다. (이렇게 오래..?.?)


```python
SELECT C.company_code, C.founder, count(distinct L.lead_manager_code), count(distinct S.senior_manager_code), count(distinct M.manager_code), count(distinct E.employee_code)

FROM Company as C, Lead_Manager as L, Senior_Manager as S, Manager as M, Employee as E

WHERE C.company_code = L.company_code
  AND L.company_code = S.company_code
  AND S.company_code = M.company_code
  AND M.company_code = E.company_code
  
GROUP BY C.company_code, C.founder
ORDER BY C.company_code 
```


```python

```

### 이 문제에서는 데이터형을 변환할 필욘 없었으나, 데이터형 변환하여 정렬하는 방법도 있다
* Cast(_as_) / Convert(_,_)
    - e.g. 1 10 2 3 4 5 6 7 8 9 ... 이걸
    - -->  1 2 3 4 5 6 7 8 9 10... 이렇게 정렬
    - ORDER BY convert(decimal, substring(company_code, 2))
    - ORDER BY cast(company_code as unsigned integer) 

![image.png](attachment:image.png)

![image.png](attachment:image.png)

-------------

### Solution(오답_처음, INNER JOIN시도)


```python
    SELECT 
    founder, count(lead_manager_code), count(senior_manager_code), 
    count(manager_code), count(employee_code)

    FROM (SELECT E.employee_code, E.manager_code, E.senior_manager_code, E.lead_manager_code, C.founder
        FROM (SELECT DISTINCT * FROM Employee) AS E
        LEFT JOIN (SELECT DISTINCT * FROM Company) AS C
        ON E.company_code = C.company_code) AS temp

    ORDER BY CAST(SUBSTR(company_code,2) AS UNSIGNED) ASC
```

![image.png](attachment:image.png)
