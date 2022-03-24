# SQL_HackerRank_Inner Join

# Average Population of Each Continent

## Problem
Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

## Solution


```python
SELECT country.continent, FLOOR(AVG(city.population)) 
FROM city
    INNER JOIN country
    ON city.countrycode = country.code 
GROUP BY country.continent
```
