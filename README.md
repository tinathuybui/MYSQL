# MYSQL
```mysql
SELECT * FROM students WHERE first_name='Bob' and postcode=2303;
SELECT DISTINCT CITY FROM STATION WHERE ( ID % 2 ) = 0;
SELECT COUNT(CITY) - COUNT(DISTINCT CITY);
(SELECT CITY, LENGTH(CITY)
FROM STATION 
ORDER BY LENGTH(CITY) ASC, CITY ASC LIMIT 1)
UNION
(SELECT  CITY, LENGTH(CITY)
FROM STATION 
ORDER BY LENGTH(CITY) DESC, CITY ASC LIMIT 1);
SELECT DISTINCT(CITY)
FROM STATION 
WHERE LEFT(CITY, 1) IN ('a', 'e', 'i', 'o', 'u');
SELECT DISTINCT (CITY)
FROM STATION
WHERE RIGHT (CITY,1) IN ('a', 'e', 'i', 'o', 'u');
SELECT DISTINCT(CITY)
FROM STATION 
WHERE LEFT(CITY,1) IN ('a', 'e', 'i', 'o', 'u')
AND
RIGHT (CITY,1) IN ('a', 'e', 'i', 'o', 'u');
SELECT DISTINCT(CITY)
FROM STATION 
WHERE NOT LEFT(CITY, 1) IN ('a', 'e', 'i', 'o', 'u');
SELECT DISTINCT(CITY)
FROM STATION 
WHERE NOT RIGHT (CITY, 1) IN ('a', 'e', 'i', 'o', 'u')
AND
NOT LEFT (CITY, 1) IN ('a', 'e', 'i', 'o', 'u');
