# SQL_HackerRank_11_Weather Observation 13-18
- problem link (https://www.hackerrank.com/challenges/weather-observation-station-13/problem?isFullScreen=true)

## 13. Problem
Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345 . Truncate your answer to  decimal places.

## Solution
    - TRUNCATE(숫자, 자릿수) : 소수점 이하 몇 자리까지 남기고 버리기
    - WHERE 절에서 BETWEEN a AND b


```python
SELECT TRUNCATE(SUM(lat_n), 4)
FROM station
WHERE lat_n BETWEEN 38.7880 AND 137.2345 
```

## 14. Problem
- Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345 . Truncate your answer to  decimal places..

## Solution


```python
SELECT TRUNCATE(MAX(LAT_N), 4)
FROM STATION
WHERE LAT_N < 137.2345
```

## 15. Problem
- Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.

## Solution
    - 반올림 ROUND(숫자, 자릿수)


```python
SELECT ROUND(long_w, 4)
FROM station
WHERE lat_n < 137.2345
ORDER BY lat_n DESC
limit 1
```

## 16. Problem
- Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places.

## Solution



```python
# 1_풀이

SELECT ROUND(MIN(lat_n), 4)
FROM station
WHERE lat_n > 38.7780
```


```python
# 2_다른 풀이

SELECT ROUND(lat_n, 4)
FROM station
WHERE lat_n > 38.7780
ORDER BY lat_n ASC
limit 1
```

## 17. Problem
- Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7880. Round your answer to  decimal places.

## Solution


```python
# 1_풀이_오답

SELECT ROUND(long_w, 4)
FROM station
WHERE MIN(lat_n) AND lat_n > 38.7880
```


```python
# 2_풀이_정답

SELECT ROUND(long_w, 4)
FROM station
WHERE lat_n > 38.7880
ORDER BY lat_n ASC LIMIT 1
```

## 18. Problem

![image.png](attachment:image.png)

## Solution
    - Manhattan distance
 : (definition) In a plane with p1 at (x1, y1) and p2 at (x2, y2), it is |x1 - x2| + |y1 - y2|.


```python
# 1_풀이_오답

SELECT ROUND(ABS(a - c) + ABS(b - d), 4)
FROM station
WHERE a = MIN(lat_n)
    AND b = MIN(long_w)
    AND c = MAX(lat_n)
    AND d = MAX(long_w)
```


```python
# 2_풀이_정답

SELECT ROUND(ABS(MIN(lat_n)- MAX(lat_n)) + ABS(MIN(long_w)- MAX(long_w)), 4)
FROM station
```
