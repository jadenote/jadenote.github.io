# SQL_HackerRank_Union

# Symmetric Pairs

## Problem
Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.
problem link (hackerrank.com/challenges/symmetric-pairs/problem?h_r=internal-search)

## Solution


```python
(1) id 순차에 따라 날짜가 커지므로, id 기준 +1 하여 Inner Join하기

SELECT today.id id
FROM weather AS today
    INNER JOIN weather AS yesterday 
    ON today.id = yesterday.id+1
WHERE today.temperature > yesterday.temperature
```


```python
(2) DATE 형식의 데이터를 계산하기

SELECT today.id id
FROM weather AS today
    INNER JOIN weather AS yesterday 
    ON today.recordDate = DATE_ADD(yesterday.recordDate, INTERVAL 1 DAY)
WHERE today.temperature > yesterday.temperature


```
