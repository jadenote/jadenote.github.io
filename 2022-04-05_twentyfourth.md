# SQL_HackerRank_Weather Observation Station 1-12

## Problem
- Query all columns for a city in CITY with the ID 1661

## Solution


```python
SELECT * FROM city
WHERE id = 1661
```

## Problem
- Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

## Solution


```python
SELECT * FROM city
WHERE countrycode = 'JPN'
```

## Problem
- Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN

## Solution


```python
SELECT name FROM city
WHERE countrycode = 'JPN'
```

## Problem
- Query a list of CITY and STATE from the STATION table.

## Solution


```python
SELECT city, state
FROM station
```

## Problem
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

## Problem
- Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

## Solution


```python
SELECT DISTINCT city FROM station
WHERE LEFT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
```

## Problem
- Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

## Solution

SELECT DISTINCT city FROM station
WHERE RIGHT(city,1) IN ('a', 'e', 'i', 'o', 'u')

## Problem
- Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

https://www.hackerrank.com/challenges/weather-observation-station-8/problem?isFullScreen=true&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen

## Solution


```python
SELECT DISTINCT city
FROM station

WHERE LEFT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
AND RIGHT(city, 1) IN ('a', 'e', 'i', 'o', 'u')
```
