# SQL_HackerRank_Inner Join

# Population Census

## Problem
Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

problem link (https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?h_r=internal-search&isFullScreen=false)

## Solution


```python
SELECT SUM(city.population)
FROM city
    INNER JOIN country
    ON city.countrycode = country.code
WHERE country.continent = 'Asia'
```
