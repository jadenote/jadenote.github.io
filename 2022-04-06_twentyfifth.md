# SQL_HackerRank_11_Weather Observation 1-12

- problem link (https://www.hackerrank.com/challenges/weather-observation-station-1/problem?isFullScreen=true)

## 1. Problem
- Query a list of CITY and STATE from the STATION table.

## Solution


```python
SELECT city, state
FROM station
```

## 2. Problem
- 2번 문제는 사이트에 없었음 - PASS

## 3. Problem
- Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

## Solution


```python
SELECT distinct city FROM station 
WHERE id % 2 = 0
```


```python
#다른 풀이
SELECT distinct city FROM station 
WHERE MOD (id, 2) = 0
```

## 4. Problem
- Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

## Solution


```python
SELECT count(city) - count(DISTINCT city)
FROM station
```

## 5. Problem
- Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

## Solution
    - UNION
    - ORDER BY 조건1 ASC/DESC ,(콤마로 연결) 조건2 ASC/DESC LIMIT 1


```python
( SELECT city, length(city)
FROM station
ORDER BY length(city) asc , city asc limit 1 )

UNION

( SELECT city, length(city)
FROM station
ORDER BY length(city) desc , city asc limit 1 )
```

## 6. Problem
- Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT city FROM station
WHERE LEFT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
```

## 7. Problem
- Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

## Solution

SELECT DISTINCT city FROM station
WHERE RIGHT(city,1) IN ('a', 'e', 'i', 'o', 'u')

## 8. Problem
- Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

## 8. Problem
- Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT city
FROM station

WHERE LEFT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
AND RIGHT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
```

## 9. Problem
- Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT city
FROM station
WHERE LEFT(city,1) NOT IN ('a','e','i','o','u')
```

## 10. Problem
- Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT city
FROM station
WHERE RIGHT(city,1) NOT IN ('a','e','i','o','u')
```

## 11. Problem
- Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT(city)
FROM station
WHERE RIGHT(city,1) NOT IN ('a','e','i','o','u')
    OR LEFT(city,1) NOT IN ('a','e','i','o','u')
```

## 12. Problem
- Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT(city)
FROM station
WHERE RIGHT(city,1) NOT IN ('a','e','i','o','u')
    AND LEFT(city,1) NOT IN ('a','e','i','o','u')
```
