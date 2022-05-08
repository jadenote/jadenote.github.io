# SQL_Leetcode_**180. Consecutive Numbers**



## [Problem](https://leetcode.com/problems/consecutive-numbers/)

---

Table: `Logs`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| num         | varchar |
+-------------+---------+
id is the primary key for this table.
id is an autoincrement column.

```

Write an SQL query to find all numbers that appear at least three times consecutively.

Return the result table in **any order**.



## Solution

---

- (이 문제에선 id를 ‘행 인덱스 번호’라고 여겨도 무방할 것 같고)
- Num(id) = Num(id+1) = Num(id+2) 인 경우를 찾는
- `self join` 하여서 교집합을 구해본다
- `Inner join`을 두 번 사용 : (처음 시도해보았는데, 된다!)  Inner join 쿼리 두 세트를 그냥 열거하여 적으면 된다
- Alias 정할 때 `as` 생략 가능하다 (쿼리 구조를 눈으로 익히는 중이어서 일부러 붙이는 중)
- select에서 ‘`DISTINCT` ’ 붙여야 한다 (처음에 안 적어줘서 오답 나왔음)

---

```sql
SELECT DISTINCT log1.num AS ConsecutiveNums 
FROM LOGS AS log1

INNER JOIN LOGS AS log2
    ON log2.id = log1.id+1
    AND log1.num = log2.num

INNER JOIN LOGS AS log3
    ON log3.id = log2.id+1
    AND log2.num = log3.num
```



## Result

---

![image](https://user-images.githubusercontent.com/99947811/167286126-98d7949d-5231-4ef1-b2f6-c55c5bc3cd9e.png)
