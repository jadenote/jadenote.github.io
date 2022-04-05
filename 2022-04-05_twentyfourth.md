# SQL_HackerRank_10

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

# SQL_HackerRank_Aggregation

## Japan Population

### Problem
Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

### Solution

SELECT SUM(population)
FROM city
WHERE countrycode = 'JPN'

## The Blunder

### Problem
키보드가 고장난 사만다의 이야기...
Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.

problem link (https://www.hackerrank.com/challenges/the-blunder/problem?isFullScreen=true)

### Solution
    - 0이 없는 계산값 : REPLACE() 사용
    - 반올림 : CEIL() 사용

SELECT CEIL(AVG(salary) - AVG(REPLACE(salary, "0", "")))
FROM employees
