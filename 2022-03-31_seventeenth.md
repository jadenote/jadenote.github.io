SQL_HackerRank_09
Weather Observation Station 5

Problem
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
problem link (https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true)

Solution
SELECT city, length(city)
FROM STATION
ORDER BY length(city) asc, city asc
limit 1;

SELECT city, length(city)
FROM STATION
ORDER BY length(city) desc, city asc
limit 1;



/* length(칼럼) 길이 함수 사용
union은 order by가 쿼리 맨 마지막에 1번 온다
--> 다른 방법으로!
*/