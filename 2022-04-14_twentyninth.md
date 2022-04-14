# SQL_HackerRank_Advanced Select
# The PADS
- problem link (https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true)

## Problem

Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.


where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

## Solution

    - LOWER() : 직업 이름을 소문자로 바꿔줘야 하는데, 알아채지 못하여 마지막에 헤맸다...
    - CONCAT() 사용하여 값 붙이기
    - 두번째 쿼리에서 COUNT(occupation) 대신 -> COUNT(*)를 써도 같은 결과값이 나온다.
    둘의 차이를 설명하지 못하는 걸로 보아, GROUP BY에 대한 이해를 보충해야 할 필요성을 느낀다. 공부.


```python
# 풀이_3차 시도_해답

SELECT CONCAT(name, '(', LEFT(occupation, 1) , ')' )
FROM occupations
ORDER BY name ;

SELECT CONCAT('There are a total of', ' ', COUNT(occupation),' ', LOWER(occupation), 's.')
FROM occupations
GROUP BY occupation
ORDER BY COUNT(occupation), occupation
```


```python
# 풀이_1차 시도_오답

SELECT name, '(', (LEFT(name, 1)), ')'
FROM occupations
ORDER BY occupation ASC ;

SELECT 'There are a total of', count(occupation), occupation, 's'
FROM occupations
GROUP BY occupation
ORDER BY occupation ASC;


# 쿼리 결과

Priyanka ( P )
Britney ( B )
Belvet ( B )
Naomi ( N )
Ashley ( A )
Jane ( J )
Jenny ( J )
Kristeen ( K )
Christeen ( C )
There are a total of 4 Actor s
There are a total of 3 Doctor s
There are a total of 7 Professor s
There are a total of 4 Singer s
```


```python
# 풀이_2차 시도_오답

-- occupation_count, occupation 칼럼을 새로 생성하기
-- 칼럼 뒤에 값 붙이기(s)
-- 괄호 안에 추출값을 넣어서 표현하기 

SELECT CONCAT(name, '(', LEFT(occupation, 1) , ')' )
FROM occupations
ORDER BY name ;

SELECT CONCAT('There are a total of', ' ', COUNT(occupation),' ', occupation, 's.')
FROM occupations
GROUP BY occupation
ORDER BY COUNT(occupation), occupation
```
