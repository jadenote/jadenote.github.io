# SQL_HackerRank_Symmetric Pairs

## Problem
Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.
problem link (hackerrank.com/challenges/symmetric-pairs/problem?h_r=internal-search)


```python
SELECT x X, y Y
FROM functions
WHERE x=y
GROUP BY x
HAVING COUNT(x=y)>1

UNION

SELECT f1.x X, f1.y Y
FROM functions AS f1
JOIN functions AS f2
ON f1.x = f2.y AND f1.y = f2.x
WHERE f1.x < f2.x
ORDER BY X
```


```python
### Expected Output
2 24 
4 22 
5 21 
6 20 
8 18 
9 17 
11 15
13 13
```


```python
- 같은 케이스 / 다른 케이스 를 UNION
- SELF JOIN
- ORDER BY는 UNION 후 맨 마지막에 적으며, 전체 테이블에 대해 적용된다
```
