# MYSQL
```mysql
SELECT * FROM students WHERE first_name='Bob' and postcode=2303;
```

```mysql
SELECT DISTINCT CITY FROM STATION WHERE ( ID % 2 ) = 0
```

```mysql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
```

```mysql
(SELECT CITY, LENGTH(CITY)
FROM STATION 
ORDER BY LENGTH(CITY) ASC, CITY ASC LIMIT 1)
UNION
(SELECT  CITY, LENGTH(CITY)
FROM STATION 
ORDER BY LENGTH(CITY) DESC, CITY ASC LIMIT 1)
```

```mysql
SELECT DISTINCT(CITY)
FROM STATION 
WHERE LEFT(CITY, 1) IN ('a', 'e', 'i', 'o', 'u')
```

```mysql
SELECT DISTINCT (CITY)
FROM STATION
WHERE RIGHT (CITY,1) IN ('a', 'e', 'i', 'o', 'u')
```

```mysql
SELECT DISTINCT(CITY)
FROM STATION 
WHERE LEFT(CITY,1) IN ('a', 'e', 'i', 'o', 'u')
AND
RIGHT (CITY,1) IN ('a', 'e', 'i', 'o', 'u')
```

```mysql
SELECT DISTINCT(CITY)
FROM STATION 
WHERE NOT LEFT(CITY, 1) IN ('a', 'e', 'i', 'o', 'u')
```

```mysql
SELECT DISTINCT(CITY)
FROM STATION 
WHERE NOT RIGHT (CITY, 1) IN ('a', 'e', 'i', 'o', 'u')
AND
NOT LEFT (CITY, 1) IN ('a', 'e', 'i', 'o', 'u')
```

```mysql
SELECT Name FROM STUDENTS 
WHERE Marks > 75
ORDER BY RIGHT (NAME,3) ASC, ID ASC
```

```mysql
SELECT name FROM Employee
WHERE salary > 2000
AND months < 10
ORDER BY employee_id ASC
```

```mysql
SELECT ROUND (MIN(LAT_N), 4)
FROM STATION
WHERE LAT_N > 38.7780
```

```mysql
SELECT ROUND (LONG_W, 4) FROM STATION 
WHERE LAT_N = (SELECT MIN (LAT_N) FROM STATION WHERE LAT_N > 38.7780)
```

```mysql
SELECT COUNT(NAME)
FROM CITY
WHERE POPULATION > 100000;

```

```mysql
select  country.continent, FLOOR(AVG(city.population)) from country
join city on city.countrycode = country.code
group by country.continent

```
```mysql
SELECT CEIL((AVG(salary)) - (AVG(REPLACE(salary, '0', '')))) FROM employees
```

```mysql
DECLARE @rows int-- Declare                   
SELECT @rows = 1 -- initialization                  
WHILE @rows <= 20 -- Condition                 
BEGIN --Begin                           
PRINT replicate('* ', @rows)--Print      
SET @rows = @rows + 1 --Set             
END --End
```

```mysql
DECLARE @rows int                  -- Declare 
SELECT @rows = 20                  -- initialization 
WHILE @rows > 0                  -- Condition
BEGIN                             -- Begin
PRINT replicate('* ', @rows)       -- Print
SET @rows = @rows - 1               -- Set
END                               -- end
               
```

```mysql
SELECT (Salary*Months)as earnings, COUNT(*) 
FROM EMPLOYEE
GROUP BY 1
ORDER By earnings DESC limit 1
```

```mysql
SELECT Students.name
From Students 
JOIN Friends on Students.ID = Friends.ID
JOIN Packages on Friends.ID = Packages.ID
JOIN Packages p2 on Friends.Friend_ID = p2.ID
Where Packages.Salary < p2.Salary
ORDER By p2.Salary
```
```mysql
SELECT C.company_code,
         C.founder,
         Count(DISTINCT E.lead_manager_code),
         Count(DISTINCT E.senior_manager_code),
         Count(DISTINCT E.manager_code),
         Count(DISTINCT E.employee_code)
FROM Company C
JOIN Employee E
WHERE C.company_code = E.company_code
GROUP BY  C.company_code, C.founder
ORDER BY  C.company_code
```
