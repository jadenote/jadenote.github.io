# HackerRank_Advanced Selcect_Occupations

### Problem
Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.
- Link(https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)

CASE 조건문을 이용하여 쿼리를 짜야한다는 건 알았는데, 각 행마다 이름을 모아 나오게 하는 방법이 어려웠다.
 * 솔루션을 구글링 해보니 INDEX번호를 셀 수 있는 변수를 세팅해야 한다는 걸 알게되었다.
 * 각 직업별 Index를 세기 위한 변수 설정
    * SET @D=0, @P=0, @S=0, @A=0;
    * 참고 (https://velog.io/@ljs7463/HackerRank-Occupations)

### SET @ 의미
    - 행번호를 부여하기 위한 변수
### @D := @D+1
    - 행이 바뀔 때마다 1씩 증가시킴
### 작성한 코드를 하나의 테이블로 취급하는 방법 -> FROM절로 넣어서 Temporary table 만들기

### Solution (해답)


```python
SET @D = 0, @P = 0, @S = 0, @A = 0;
SELECT MAX(Doctor), MAX(Professor), MAX(Singer), MAX(Actor)
FROM (SELECT
       CASE WHEN Occupation = 'Doctor' THEN Name END AS Doctor,
       CASE WHEN Occupation = 'Professor' THEN Name END AS Professor, 
       CASE WHEN Occupation = 'Singer' THEN Name END AS Singer,
       CASE WHEN Occupation = 'Actor' THEN Name END AS Actor,
       CASE 
            WHEN Occupation = 'Doctor' THEN (@D:=@D+1)
            WHEN Occupation = 'Professor' THEN (@P:=@P+1)
            WHEN Occupation = 'Singer' THEN (@S:=@S+1)
            WHEN Occupation = 'Actor' THEN (@A:=@A+1)
       END AS Count
FROM Occupations
ORDER BY Name) AS tempTable
GROUP BY Count
```

![image.png](attachment:image.png)

### Solution (오답_첫번째시도)


```python
SELECT CASE WHEN Occupation = 'Doctor' THEN Name END AS Doctor,
       CASE WHEN Occupation = 'Professor' THEN Name END AS Professor, 
       CASE WHEN Occupation = 'Singer' THEN Name END AS Singer, 
       CASE WHEN Occupation = 'Actor' THEN Name END AS Actor
FROM Occupations
ORDER BY Name
```

* 오류 이유 : NULL값으로 인해 각각 다른 행에 Name이 있음
    --> 한 행에 이름이 모여 있도록 수정 필요
    --> MAX('Amina', NULL, NULL, NULL) => 'Amina'가 맨 윗줄로 정렬된다! 이걸 이용
![image.png](attachment:image.png)

### Solution (오답_두번째시도)


```python
SET @D = 0, @P = 0, @S = 0, @A = 0;

SELECT CASE WHEN Occupation = 'Doctor' THEN Name END AS Doctor,
       CASE WHEN Occupation = 'Professor' THEN Name END AS Professor, 
       CASE WHEN Occupation = 'Singer' THEN Name END AS Singer,
       CASE WHEN Occupation = 'Actor' THEN Name END AS Actor,
       CASE 
            WHEN Occupation = 'Doctor' THEN (@D:=@D+1)
            WHEN Occupation = 'Professor' THEN (@P:=@P+1)
            WHEN Occupation = 'Singer' THEN (@S:=@S+1)
            WHEN Occupation = 'Actor' THEN (@A:=@A+1)
       END AS Count   
FROM Occupations
ORDER BY Name
```


      Input In [2]
        오답_첫번째시도SET @D = 0, @P = 0, @S = 0, @A = 0;
                            ^
    SyntaxError: invalid syntax
    


![image.png](attachment:image.png)

* 추가로, 구글링해보니, PARTITION BY 로 푸는 방법도 있던데, 추후 보충 공부 해보자
