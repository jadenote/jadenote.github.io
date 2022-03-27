# SQL_LeetCode_Left Join

# 183. Customers Who Never Order

## Problem
Write an SQL query to report all customers who never order anything.

Return the result table in any order.

problem link (https://leetcode.com/problems/customers-who-never-order/submissions/)

## Solution


```python
# (1) LEFT JOIN

SELECT *
FROM customers
    LEFT JOIN orders
    ON customers.id = orders.customerId
    
{"headers":["id", "name", "id", "customerId"]
"values": [[1, "Joe", 2, 1],
           [2, "Henry", null, null],
           [3, "Sam", 1, 3],
           [4, "Max", null, null]]}
```


```python
# (2) WHERE, ALIAS

SELECT customer.name AS Customers -- LeetCode에서는 OUTPUT 칼럼명까지 alias 정확하게 맞춰줘야 함
FROM customers
    LEFT JOIN orders
    ON customers.id = orders.customerId
WHERE orders.id is NULL
```
