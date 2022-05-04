# SQL_HackerRank_Weather Observation 19-20
- problem link (https://www.hackerrank.com/challenges/weather-observation-station-19/problem?isFullScreen=true)

![image.png](attachment:image.png)

## 19. Problem
![image.png](attachment:image.png)

## Solution

    - ROUND 함수를 사용함 (FORMAT(소수, 소숫점이하 자릿수) : 버림 기능)
    - 처음 풀이 틀렸어서 헤맸던 이유 : 괄호(괄호가 많아질 때, 자세히 보자)
    - Euclidean distance : 
![image.png](attachment:image.png)

#### Solution


```python
SELECT ROUND(
        SQRT( POWER(MAX(lat_n)-MIN(lat_n), 2) + POWER(MAX(long_w)-MIN(long_w),2) )
        , 4)
FROM station
```

---

## 20. Problem
- A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to  decimal places.

- problem link (https://www.hackerrank.com/challenges/weather-observation-station-20/problem?isFullScreen=true)

## Solution
첫 번째 시도 (정답이지만 오답임)
#### (MySQL에서는 Oracle과 달리 Median함수가 지원되지 않음)
#### 행을 카운팅(1씩 증가)하는 변수 선언 : set @row_num = 0


```python
set @row_num = 0;

SELECT ROUND(LAT_N, 4) AS Median
FROM (SELECT @row_num := @row_num +1 as RowNumber, LAT_N FROM station ORDER BY LAT_N) AS Sub 
WHERE Sub.RowNumber in ((@row_num+1) / 2)
```

![image-2.png](attachment:image-2.png)

### 정답..이지만 오답인 이유 : 인덱스 수가 홀수, 짝수인 경우 둘 다 고려해서 쿼리짜기
- 위 쿼리로 문제 정답은 맞았으나, 
    - 중앙값을 찾을 때 데이터 개수(인덱스 수)가 홀수/짝수에 따라 설정 방법이 달라짐
    - count(*) = 499, 즉, '홀수' 였기에 가능했음  (Median = (499 + 1)/2로 딱 떨어졌던 케이스)
    - 만약, 짝수였다면 틀렸을 것

## => Solution
##### 수정사항 
- set @row_num 초기값을 -1 로 설정 --> 행 인덱스 0부터 시작되도록 만듦 (인덱스가 1부터 나오면, +1을 해야하는 등 쿼리가 좀 복잡해지더군요)
- 인덱스 개수가 짝수일 때 : FLOOR()값과 CEIL()의 AVG() 평균값을 Median으로 반환
   - (e.g. RowNumber=3 이며 인덱스 개수=4 일 때 :  RowNumber인 3 %  2 = 1.5가 됨 --> 이를 FLOOR(반내림)=1, CEIL(반올림)= 2가 됨 --> 이 둘의 평균값을 구하도록 함)
- 인덱스 개수가 홀수일 때 : FLOOR()값 = CEIL()값 = Median
   - 참고: https://techblog-history-younghunjo1.tistory.com/160


```python
set @row_num = -1;

SELECT ROUND(AVG(LAT_N), 4) AS Median
FROM (SELECT @row_num := @row_num +1 as RowNumber, LAT_N FROM station ORDER BY LAT_N) AS Sub 
WHERE Sub.RowNumber in (FLOOR(@row_num)/2, CEIL(@row_num)/2)
```

![image-2.png](attachment:image-2.png)

## Solution
또 다른 풀이 방법 : PERCENT_RANK() 함수 사용할 수도 있음
  - PERCENT_RANK는 해당 그룹 안에서의 백분위 순위(Percentil Rank)를 반환함
  - 0이상 1이하의 값을 반환함 --> 즉, 중위값 median을 구하려면, 0.5를 구하면 됨.
  - Syntax
    - PERCENT_RANK() OVER ([partition_by_clause] order_by_clause)


```python

```
