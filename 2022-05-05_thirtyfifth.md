# HackerRank_SQL_Basic Join

# The Report

## Problem
Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

Link(https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true)

## Solution

### 이 문제를 풀면서, Join 사용법에 대해 지금까지 몰랐던 부분을 알게 됨
* 기존 - 두 테이블의 '공통 칼럼'을 기준으로 (On table1.column = table2.column 형식)으로 묶는 방법
* 알게 된 점 - '범위'(between __ and __)를 가지고 매핑하는 방법
    - ' JOIN g.Grades ON s.Marks BETWEEN g.Min_Mark AND g.Max_Mark ' 
    - JOIN 에서 'On' 대신 'Where'을 써도 작동했음

### 서로 다른 3가지 방법으로 풀어봄

### Solution 01
    - if(조건, 참 반환값, 거짓 반환값) 구문 사용


```python
SELECT IF(g.GRADE < 8, NULL, s.Name), g.Grade, s.Marks
    FROM Students AS s
    JOIN Grades AS g
    ON s.Marks BETWEEN g.Min_Mark AND g.Max_Mark 
ORDER BY g.Grade DESC, s.Name, s.Marks
```


### Solution 02
    - 칼럼 Alias를 사용하지 않은 쿼리도 가능
    - 이 문제에서 두 테이블 (Students, Grades)에 공통 칼럼이 존재하지 않으므로 --> 칼럼명 앞에 Alias를 써서 구분하지 않고 심플한 쿼리도 가능함


```python
SELECT IF (GRADE < 8, NULL, Name), Grade, Marks
    FROM Students
    JOIN Grades
WHERE Marks BETWEEN Min_Mark AND Max_Mark 
ORDER BY Grade DESC, Name, Marks
```



### Solution 03
    - CASE WHEN ELSE END 구문 사용


```python
SELECT CASE WHEN GRADE < 8 THEN NULL Else Name END, Grade, Marks
    FROM Students
    JOIN Grades
WHERE Marks BETWEEN Min_Mark AND Max_Mark 
ORDER BY Grade DESC, Name, Marks
```



![image](https://user-images.githubusercontent.com/99947811/166919296-8e5d2579-55ec-4c77-bc50-613535ecb096.png)
