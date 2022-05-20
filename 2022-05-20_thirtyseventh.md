## SQL_HakcerRank_Top Competitors

### Problem
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.

Link(https://www.hackerrank.com/challenges/full-score/problem?isFullScreen=true)

### Solution
- 헤맸던 이유 : 
    - 문제랑 점수테이블 보고 '만점 = 120 점'이라고 잘못 이해했음....
    - difficulty 테이블과 challenges 테이블 조인하여 난이도 별 만점 점수 확인해야함


```python
SELECT h.hacker_id, h.name
FROM submissions s
    JOIN hackers h
    ON s.hacker_id = h.hacker_id
        
    JOIN challenges c
    ON s.challenge_id = c.challenge_id

    JOIN difficulty d
    ON c.difficulty_level = d.difficulty_level

WHERE d.score = s.score

GROUP BY h.hacker_id, h.name
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC,  h.hacker_id ASC
```

![image.png](attachment:image.png)


```python

```
