ERD - 테이블 간의 관계를 도식화 한 것 , 조인할 때 어떤 칼럼으로 연결되는지 알 수 있음

# SQL_HackerRank_Inner Join

# African Cities

## Problem
Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

## Solution


```python
SELECT city.name
FROM city
     INNER JOIN country
     ON city.CountryCode = country.Code
WHERE country.continent = 'Africa'
```
