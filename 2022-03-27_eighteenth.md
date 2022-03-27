# SQL_LeetCode_Self Join

# 181. Employees Earning More Than Their Managers

## Problem
Write an SQL query to find the employees who earn more than their managers.

Return the result table in any order.

problem link(https://leetcode.com/problems/employees-earning-more-than-their-managers/)

## Solution


```python
-- (1)평사원테이블 매니저테이블 두개로 만든다 INNER JOIN
-- (2)평사원샐러리칼럼 매니저샐러리칼럼 비교한다

SELECT employee.name AS Employee
FROM employee
    INNER JOIN employee AS manager
    on employee.managerId = manager.Id
WHERE employee.salary > manager.salary
```
