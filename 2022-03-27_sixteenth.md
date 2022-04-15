# SQL_LeetCode_Pivoting

# 1179.Reformat Department Table
결과값을 가로로 보기

## Problem
Write an SQL query to reformat the table such that there is a department id column and a revenue column for each month.
Return the result table in any order.

problem link (https://leetcode.com/problems/reformat-department-table/)

## Solution
-- SUM으로 CASE조건 묶기
-- ID로 묶어서 정렬


```python
SELECT id,
    SUM(CASE WHEN month = 'Jan' THEN revenue ELSE NULL END) AS Jan_Revenue
  , SUM(CASE WHEN month = 'Feb' THEN revenue ELSE NULL END) AS Feb_Revenue
  , SUM(CASE WHEN month = 'Mar' THEN revenue ELSE NULL END) AS Mar_Revenue
  , SUM(CASE WHEN month = 'Apr' THEN revenue ELSE NULL END) AS Apr_Revenue
  , SUM(CASE WHEN month = 'May' THEN revenue ELSE NULL END) AS May_Revenue
  , SUM(CASE WHEN month = 'Jun' THEN revenue ELSE NULL END) AS Jun_Revenue
  , SUM(CASE WHEN month = 'Jul' THEN revenue ELSE NULL END) AS Jul_Revenue
  , SUM(CASE WHEN month = 'Aug' THEN revenue ELSE NULL END) AS Aug_Revenue
  , SUM(CASE WHEN month = 'Sep' THEN revenue ELSE NULL END) AS Sep_Revenue
  , SUM(CASE WHEN month = 'Oct' THEN revenue ELSE NULL END) AS Oct_Revenue
  , SUM(CASE WHEN month = 'Nov' THEN revenue ELSE NULL END) AS Nov_Revenue
  , SUM(CASE WHEN month = 'Dec' THEN revenue ELSE NULL END) AS Dec_Revenue
FROM department
GROUP BY id ;
```
