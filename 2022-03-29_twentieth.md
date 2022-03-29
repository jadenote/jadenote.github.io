# SQL_LeetCode

# 197. Rising Temperature

## Problem
Write an SQL query to find all dates' Id with higher temperatures compared to its previous dates (yesterday).
Return the result table in any order.

problem link(https://leetcode.com/problems/rising-temperature/)

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
