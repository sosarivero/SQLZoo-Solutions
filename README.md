# SQL Zoo Solutions
SQL Zoo is a comprehensive SQL tutorial covering fundamental concepts and advanced queries, offering interactive exercises and examples to reinforce learning. It provides a structured approach to mastering SQL commands, enabling users to develop proficiency in database querying and manipulation.

Here are the solution queries I wrote for every section of the tutorial.

- [SQL Zoo Solutions](#sql-zoo-solutions)
  - [SELECT basics](#select-basics)
  - [SELECT names](#select-names)
  - [SELECT from world](#select-from-world)
  - [SELECT from nobel](#select-from-nobel)
  - [SELECT in SELECT](#select-in-select)
  - [SUM and COUNT](#sum-and-count)
  - [JOIN](#join)
  - [More JOIN](#more-join)
  - [Using NULL](#using-null)
  - [Self JOIN](#self-join)


## SELECT basics
[Back to the top](#sql-zoo-solutions)

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
[Back to the top](#sql-zoo-solutions)

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
[Back to the top](#sql-zoo-solutions)

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
[Back to the top](#sql-zoo-solutions)

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
## SELECT in SELECT
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    select NAME from world
    WHERE population > (
        SELECT population FROM world
        WHERE name = 'Russia'
    );
    ```
2. 
    ```sql
    SELECT name FROM world
    WHERE continent = 'Europe'
    AND gdp/population > (
        SELECT gdp/population FROM world
        WHERE name = 'United Kingdom'
    );
    ```
3. 
    ```sql
    SELECT name, continent FROM world
    WHERE continent IN (
        SELECT continent FROM world
        WHERE name IN ('Argentina', 'Australia')
    );
    ```
4. 
    ```sql
    SELECT name, population FROM world
    WHERE population > (
        SELECT population FROM world
        WHERE name = 'United Kingdom'
    ) AND population < (
        SELECT population FROM world
        WHERE name = 'Germany'
    );
    ```
5. 
    ```sql
    SELECT name,
        CONCAT(
            ROUND(population / (
                SELECT population 
                FROM world 
                WHERE name = 'Germany'
            ) * 100), '%'
        ) AS percentage
    FROM world
    WHERE continent = 'Europe';
    ```
6. 
    ```sql
    SELECT name FROM world
    WHERE gdp > ALL(
        SELECT gdp FROM world
        WHERE gdp IS NOT NULL
        AND continent = 'Europe'
        );
    ```
7. 
    ```sql
    SELECT continent, name, area FROM world i
    WHERE area >= ALL(
        SELECT area FROM world j
        WHERE i.continent = j.continent
    );
    ```
8. 
    ```sql
    SELECT continent, MIN(name) AS name
    FROM world
    GROUP BY continent
    ORDER BY name;
    ```
9. 
    ```sql
    SELECT name, continent, population
    FROM world
    WHERE continent IN (
        SELECT continent FROM world i
        WHERE (
            SELECT SUM(population) FROM world j
            WHERE i.continent = j.continent
            ) <= 25000000
    );
    ```
10. 
    ```sql
    SELECT name, continent FROM world i
    WHERE population  >= ALL(
        SELECT 3 * MAX( population) FROM world j
        WHERE i.continent = j.continent AND i.name != j.name
    );
    ```
## SUM and COUNT
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    SELECT SUM(population)
    FROM world;
    ```
2. 
    ```sql
    SELECT DISTINCT continent FROM world;
    ```
3. 
    ```sql
    SELECT SUM(gdp) FROM world
    WHERE continent = 'Africa';
    ```
4. 
    ```sql
    SELECT COUNT(name) FROM world
    WHERE area >= 1000000;
    ```
5. 
    ```sql
    SELECT SUM(population) FROM world
    WHERE name IN ('Estonia', 'Latvia', 'Lithuania');
    ```
6. 
    ```sql
    SELECT continent, COUNT(name)
    FROM world
    GROUP BY continent;
    ```
7. 
    ```sql
    SELECT continent, COUNT(name)
    FROM world
    WHERE population >= 10000000
    GROUP BY continent;
    ```
8. 
    ```sql
    SELECT continent
    FROM world
    GROUP BY continent
    HAVING SUM(population) >= 100000000;
    ```
## JOIN
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    SELECT matchid, player FROM goal
    WHERE teamid = 'GER';
    ```
2. 
    ```sql
    SELECT id, stadium, team1, team2
    FROM game
    WHERE id = 1012;
    ```
3. 
    ```sql
    SELECT player, teamid, stadium, mdate
    FROM goal
    JOIN game ON id = matchid
    WHERE teamid = 'GER';
    ```
4. 
    ```sql
    SELECT team1, team2, player
    FROM goal
    JOIN game ON game.id = goal.matchid
    WHERE goal.player LIKE 'Mario%';
    ```
5. 
    ```sql
    SELECT player, teamid, coach, gtime
    FROM goal
    JOIN game ON goal.matchid = id
    JOIN eteam
    ON eteam.id = goal.teamid
    WHERE goal.gtime <= 10;
    ```
6. 
    ```sql
    SELECT mdate, teamname
    FROM game
    JOIN eteam ON eteam.id = game.team1
    WHERE coach = 'Fernando Santos';
    ```
7. 
    ```sql
    SELECT player
    FROM goal
    JOIN game ON matchid = id
    WHERE stadium = 'National Stadium, Warsaw';
    ```
8. 
    ```sql
    SELECT DISTINCT player FROM goal
    JOIN game ON goal.matchid = game.id
    WHERE goal.teamid != 'GER'
    AND (game.team1 = 'GER' OR game.team2 = 'GER');
    ```
9. 
    ```sql
    SELECT eteam.teamname, COUNT(goal.teamid)
    FROM goal
    JOIN eteam ON goal.teamid = eteam.id
    GROUP BY teamname;
    ```
10. 
    ```sql
    SELECT game.stadium, COUNT(goal.matchid)
    FROM game
    JOIN goal ON goal.matchid = game.id
    GROUP BY stadium;
    ```
11. 
    ```sql
    SELECT goal.matchid, game.mdate, COUNT(goal.matchid)
    FROM goal
    JOIN game ON game.id = goal.matchid
    WHERE game.team1 = 'POL' OR game.team2 = 'POL'
    GROUP BY matchid;
    ```
12. 
    ```sql
    SELECT game.id, mdate, COUNT(teamid)
    FROM game
    JOIN goal ON goal.matchid = game.id
    WHERE goal.teamid = 'GER'
    GROUP BY matchid;
    ```
13. 
    ```sql
    SELECT mdate,
        team1,
        SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) AS score1,
        team2,
        SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) AS score2
    FROM game
    LEFT JOIN goal ON matchid = id
    GROUP BY matchid, mdate
    ORDER BY mdate, matchid, team1, team2;
    ```
## More JOIN
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    SELECT movie.id, movie.title
    FROM movie
    WHERE movie.yr = 1962;
    ```
2. 
    ```sql
    SELECT yr FROM movie
    WHERE title = 'Citizen Kane';
    ```
3. 
    ```sql
    SELECT id, title, yr FROM movie
    WHERE title LIKE 'Star Trek%'
    ORDER BY yr;
    ```
4. 
    ```sql
    SELECT id FROM actor
    WHERE name = 'Glenn Close';
    ```
5. 
    ```sql
    SELECT id FROM movie
    WHERE title = 'Casablanca';
    ```
6. 
    ```sql
    SELECT actor.name
    FROM actor
    JOIN casting ON actor.id = casting.actorid
    JOIN movie ON casting.movieid = movie.id
    WHERE movie.title = 'Casablanca';
    ```
7. 
    ```sql
    SELECT actor.name
    FROM actor
    JOIN casting ON actor.id = casting.actorid
    JOIN movie ON casting.movieid = movie.id
    WHERE movie.title = 'Alien';
    ```
8. 
    ```sql
    SELECT title FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE actor.name = 'Harrison Ford';
    ```
9. 
    ```sql
    SELECT title FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE actor.name = 'Harrison Ford'
    AND casting.ord != 1;
    ```
10. 
    ```sql
    SELECT title, name FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE ord=1 AND yr=1962;
    ```
11. 
    ```sql
    SELECT yr, COUNT(*)
    FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE name = 'Rock Hudson'
    GROUP BY yr
    HAVING COUNT(*) > 2;
    ```
12. 
    ```sql
    SELECT title, name FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE movieid IN (
        SELECT movie.id FROM movie
        JOIN casting ON movie.id = casting.movieid
        JOIN actor ON casting.actorid = actor.id
        WHERE name = 'Julie Andrews'
    ) AND ord=1;
    ```
13. 
    ```sql
    SELECT name FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE ord=1
    GROUP BY name
    HAVING COUNT(*) >= 15;
    ```
14. 
    ```sql
    SELECT title, COUNT(actorid)
    FROM movie
    JOIN casting ON movie.id = casting.movieid
    WHERE yr = 1978
    GROUP BY movieid
    ORDER BY COUNT(actorid) DESC, title;
    ```
15. 
    ```sql
    SELECT name FROM movie
    JOIN casting ON movie.id = casting.movieid
    JOIN actor ON casting.actorid = actor.id
    WHERE name != 'Art Garfunkel'
    AND movieid IN (
        SELECT movieid FROM movie
        JOIN casting ON movie.id = casting.movieid
        JOIN actor ON casting.actorid = actor.id
        WHERE name = 'Art Garfunkel'
    );
    ```
## Using NULL
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    SELECT name FROM teacher
    WHERE dept IS NULL;
    ```
2. 
    ```sql
    SELECT teacher.name, dept.name
    FROM teacher
    INNER JOIN dept ON (teacher.dept = dept.id);
    ```
3. 
    ```sql
    SELECT teacher.name, dept.name
    FROM teacher
    LEFT JOIN dept ON (teacher.dept = dept.id);
    ```
4. 
    ```sql
    SELECT teacher.name, dept.name
    FROM teacher
    RIGHT JOIN dept ON (teacher.dept = dept.id);
    ```
5. 
    ```sql
    SELECT name, COALESCE(mobile, '07986 444 2266') FROM teacher;
    ```
6. 
    ```sql
    SELECT teacher.name, COALESCE(dept.name, 'None')
    FROM teacher
    LEFT JOIN dept ON teacher.dept = dept.id;
    ```
7. 
    ```sql
    SELECT COUNT(id), COUNT(mobile) FROM teacher;
    ```
8. 
    ```sql
    SELECT dept.name, COUNT(teacher.id)
    FROM teacher
    RIGHT JOIN dept ON teacher.dept = dept.id
    GROUP BY dept.name;
    ```
9. 
    ```sql
    SELECT name,
        CASE
            WHEN dept BETWEEN 1 AND 2 THEN 'Sci'
            ELSE 'Art'
        END
    FROM teacher;
    ```
10. 
    ```sql
    SELECT name,
        CASE
            WHEN dept BETWEEN 1 AND 2 THEN 'Sci'
            WHEN dept = 3 THEN 'Art'
            ELSE 'None'
        END
    FROM teacher;
    ```
## Self JOIN
[Back to the top](#sql-zoo-solutions)

1. 
    ```sql
    SELECT COUNT(id) FROM stops;
    ```
2. 
    ```sql
    SELECT id FROM stops
    WHERE name = 'Craiglockhart';
    ```
3. 
    ```sql
    SELECT id, name FROM stops
    JOIN route ON id = route.stop
    WHERE company = 'LRT' AND num = '4';
    ```
4. 
    ```sql
    SELECT company, num, COUNT(*)
    FROM route WHERE stop=149 OR stop=53
    GROUP BY company, num
    HAVING COUNT(*) = 2;
    ```
5. 
    ```sql
    SELECT a.company, a.num, a.stop, b.stop
    FROM route AS a
    JOIN route AS b
    ON (a.company=b.company AND a.num=b.num)
    WHERE a.stop = 53 AND b.stop = 149;
    ```
6. 
    ```sql
    SELECT a.company, a.num, stopa.name, stopb.name
    FROM route AS a
    JOIN route AS b
    ON (a.company = b.company AND a.num = b.num)
    JOIN stops AS stopa
    ON (a.stop = stopa.id)
    JOIN stops AS stopb
    ON (b.stop = stopb.id)
    WHERE stopa.name='Craiglockhart'
    AND stopb.name='London Road';
    ```
7. 
    ```sql
    SELECT DISTINCT a.company, a.num
    FROM route AS a
    JOIN route AS b
    ON a.company = b.company AND a.num = b.num
    JOIN stops AS stopa
    ON a.stop = stopa.id
    JOIN stops AS stopb
    ON b.stop = stopb.id
    WHERE stopa.id = 115
    AND stopb.id = 137;
    ```
8. 
    ```sql
    SELECT DISTINCT a.company, a.num
    FROM route AS a
    JOIN route AS b
    ON a.company = b.company AND a.num = b.num
    JOIN stops AS stopa
    ON a.stop = stopa.id
    JOIN stops AS stopb
    ON b.stop = stopb.id
    WHERE stopa.name = 'Craiglockhart'
    AND stopb.name = 'Tollcross';
    ```
9. 
    ```sql
    SELECT DISTINCT stopb.name, a.company, a.num
    FROM route AS a
    JOIN route AS b
    ON a.company = b.company AND a.num = b.num
    JOIN stops AS stopa
    ON a.stop = stopa.id
    JOIN stops AS stopb
    ON b.stop = stopb.id
    WHERE stopa.name = 'Craiglockhart';
    ```
10. 
    ```sql
    SELECT x.num, x.company, x.name, y.num, y.company
    FROM (
        SELECT DISTINCT stopa.name, a.company, a.num
        FROM route AS a
        JOIN route AS b
        ON (a.company = b.company AND a.num = b.num)
        JOIN stops AS stopa
        ON a.stop = stopa.id
        JOIN stops AS stopb
        ON b.stop = stopb.id
        WHERE stopb.name = 'Craiglockhart'
    ) AS x
    JOIN (
        SELECT DISTINCT stopc.name, c.company, c.num
        FROM route AS c
        JOIN route AS d
        ON (c.company = d.company AND c.num = d.num)
        JOIN stops AS stopc
        ON c.stop = stopc.id
        JOIN stops AS stopd
        ON d.stop = stopd.id
        WHERE stopd.name = 'Lochend' 
    ) AS y
    ON x.name = y.name
    ORDER BY x.num, name, y.num;
    ```