# SQL Zoo Solutions
SQL Zoo is a comprehensive SQL tutorial covering fundamental concepts and advanced queries, offering interactive exercises and examples to reinforce learning. It provides a structured approach to mastering SQL commands, enabling users to develop proficiency in database querying and manipulation.

Here are the solution queries I wrote for every section of the tutorial.

## SELECT basics
1.  ```sql
    SELECT population FROM world
    WHERE name = 'Germany';
    ```
2. 
    ```sql
    SELECT name, population FROM world
    WHERE name IN ('Sweden', 'Norway', 'Denmark');
    ```
3. 
    ```sql
    SELECT name, area FROM world
    WHERE area BETWEEN 200000 AND 250000;
    ```

## SELECT names
1. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE 'y%';
    ```
2. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%y';
    ```
3. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%x%';
    ```
4. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%land';
    ```
5. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE 'c%'
    AND name LIKE '%ia';
    ```
6. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%oo%';
    ```
7. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%a%a%a%';
    ```
8. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '_t%';
    ```
9. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '%o__o%';
    ```
10. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE '____';
    ```
11. 
    ```sql
    SELECT name FROM world
    WHERE name = capital;
    ```
12. 
    ```sql
    SELECT name FROM world
    WHERE capital LIKE CONCAT(name, ' ', 'city');
    ```
13. 
    ```sql
    SELECT capital, name FROM world
    WHERE capital LIKE CONCAT('%', name, '%');
    ```
14. 
    ```sql
    SELECT capital, name FROM world
    WHERE capital LIKE CONCAT(name, '%')
    AND capital != name;
    ```
15. 
    ```sql
    SELECT name, REPLACE(capital, name, '') AS extension
    FROM world
    WHERE capital LIKE CONCAT(name, '%')
    AND capital != name;
    ```

## SELECT from world
1. 
    ```sql
    SELECT name, continent, population FROM world;
    ```
2. 
    ```sql
    SELECT name FROM world
    WHERE population > 200000000;
    ```
3. 
    ```sql
    SELECT name, gdp/population
    FROM world
    WHERE population > 200000000;
    ```
4. 
    ```sql
    SELECT name, population/1000000 AS 'pop/millions'
    FROM world
    WHERE continent = 'South America';
    ```
5. 
    ```sql
    SELECT name, population FROM world
    WHERE name IN ('France', 'Germany', 'Italy');
    ```
6. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE "%united%";
    ```
7. 
    ```sql
    SELECT name, population, area
    FROM world
    WHERE area > 3000000
    OR population > 250000000;
    ```
8. 
    ```sql
    SELECT name, population, area
    FROM world
    WHERE area > 3000000
    XOR population > 250000000;
    ```
9. 
    ```sql
    SELECT name, ROUND(population/1000000, 2), ROUND(gdp/1000000000, 2)
    FROM world
    WHERE continent = 'South America';
    ```
10. 
    ```sql
    SELECT name, ROUND(gdp/population, -3)
    FROM world
    WHERE gdp > 1000000000000;
    ```
11. 
    ```sql
    SELECT name, capital FROM world
    WHERE LENGTH(name) = LENGTH(capital);
    ```
12. 
    ```sql
    SELECT name, capital FROM world
    WHERE LEFT(name, 1) = LEFT(capital, 1)
    AND name != capital;
    ```
13. 
    ```sql
    SELECT name FROM world
    WHERE name LIKE "%a%"
    AND name LIKE "%e%" AND name LIKE "%i%"
    AND name LIKE "%o%" AND name LIKE "%u%"
    AND name NOT LIKE "% %";
    ```
## SELECT from nobel
1. 
    ```sql
    SELECT yr, subject, winner
    FROM nobel
    WHERE yr = 1950;
    ```
2. 
    ```sql
    SELECT winner FROM nobel
    WHERE yr = 1962
    AND subject = 'literature';
    ```
3. 
    ```sql
    SELECT yr, subject FROM nobel
    WHERE winner = 'Albert Einstein';
    ```
4. 
    ```sql
    SELECT winner FROM nobel
    WHERE subject = 'peace'
    AND yr >= 2000;
    ```
5. 
    ```sql
    SELECT * FROM nobel
    WHERE subject = 'literature'
    AND yr BETWEEN 1980 AND 1989;
    ```
6. 
    ```sql
    SELECT * FROM nobel
    WHERE winner IN ('Theodore Roosevelt', 'Thomas Woodrow Wilson', 'Jimmy Carter', 'Barack Obama');
    ```
7. 
    ```sql
    SELECT winner FROM nobel
    WHERE winner LIKE 'John%';
    ```
8. 
    ```sql
    SELECT * FROM nobel
    WHERE (subject = 'physics' AND yr = 1980)
    OR (subject = 'chemistry' AND yr = 1984);
    ```
9. 
    ```sql
    SELECT * FROM nobel
    WHERE yr = 1980
    AND subject NOT IN ('chemistry', 'medicine');
    ```
10. 
    ```sql
    SELECT * FROM nobel
    WHERE (subject = 'medicine' AND yr < 1910)
    OR (subject = 'literature' AND yr >= 2004);
    ```
11. 
    ```sql
    SELECT * FROM nobel
    WHERE winner LIKE 'PETER GRÜNBERG';
    ```
12. 
    ```sql
    SELECT * FROM nobel
    WHERE winner LIKE 'EUGENE O''NEILL';
    ```
13. 
    ```sql
    SELECT winner, yr, subject FROM nobel
    WHERE winner LIKE 'sir%'
    ORDER BY yr DESC, winner;
    ```
14. 
    ```sql
    SELECT winner, subject FROM nobel
    WHERE yr = 1984
    ORDER BY subject IN ('chemistry', 'physics'), subject, winner;
    ```
