# Review_HackerRank_Type of Triangle

![image-2.png](attachment:image-2.png)


```python
* Solution

SELECT CASE
WHEN A=B AND B=C AND C=A THEN 'Equilateral'
WHEN A+B <= C OR B+C <= A OR C+A <= B THEN 'Not A Triangle' 
# 세변 길이 20, 20, 40 -> 삼각형이 아닌 경우를 이 쿼리 줄에서 걸러야 한다

WHEN A=B OR B=C OR C=A THEN 'Isosceles'

ELSE 'Scalene' END
FROM TRIANGLES
```


---------------------

# Review_LeetCode_1179. Reformat Department Table
    : 값을 가로로 펼쳐보기 / 엑셀 피봇팅 기능과 유사

Write an SQL query to reformat the table such that there is a department id column and a revenue column for each month.

Return the result table in any order.

https://leetcode.com/problems/reformat-department-table/


```python
SELECT ID
    ,SUM(CASE WHEN month = 'Jan' THEN revenue ELSE null END) as Jan_Revenue
    ,SUM(CASE WHEN month = 'Feb' THEN revenue ELSE null END) as Feb_Revenue 
    ,SUM(CASE WHEN month = 'Mar' THEN revenue ELSE null END) as Mar_Revenue  
    ,SUM(CASE WHEN month = 'Apr' THEN revenue ELSE null END) as Apr_Revenue 
    ,SUM(CASE WHEN month = 'May' THEN revenue ELSE null END) as May_Revenue 
    ,SUM(CASE WHEN month = 'Jun' THEN revenue ELSE null END) as Jun_Revenue 
    ,SUM(CASE WHEN month = 'Jul' THEN revenue ELSE null END) as Jul_Revenue 
    ,SUM(CASE WHEN month = 'Aug' THEN revenue ELSE null END) as Aug_Revenue
    ,SUM(CASE WHEN month = 'Sep' THEN revenue ELSE null END) as Sep_Revenue
    ,SUM(CASE WHEN month = 'Oct' THEN revenue ELSE null END) as Oct_Revenue
    ,SUM(CASE WHEN month = 'Nov' THEN revenue ELSE null END) as Nov_Revenue
    ,SUM(CASE WHEN month = 'Dec' THEN revenue ELSE null END) as Dec_Revenue 
FROM Department
GROUP BY ID
```

![image.png](attachment:image.png)

![image.png](attachment:image.png)

![image.png](attachment:image.png)
