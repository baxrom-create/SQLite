# SQLite
Homework
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER,
    length_minutes INTEGER
);
INSERT INTO movies VALUES
(1,'Toy Story','John Lasseter',1995,81),
(2,'A Bug''s Life','John Lasseter',1998,95),
(3,'Toy Story 2','John Lasseter',1999,93),
(4,'Monsters, Inc.','Pete Docter',2001,92),
(5,'Finding Nemo','Andrew Stanton',2003,107),
(6,'The Incredibles','Brad Bird',2004,116),
(7,'Cars','John Lasseter',2006,117),
(8,'Ratatouille','Brad Bird',2007,115),
(9,'WALL-E','Andrew Stanton',2008,104),
(10,'Up','Pete Docter',2009,101),
(11,'Toy Story 3','Lee Unkrich',2010,103),
(12,'Cars 2','John Lasseter',2011,120),
(13,'Brave','Brenda Chapman',2012,102),
(14,'Monsters University','Dan Scanlon',2013,110);
#1 задания
#1.Find the title of each film
#2.Find the director of each film
#3.Find the title and director of each film
#4.Find the title and year of each film
#5.Find all the information about each film
#Решение
SELECT title FROM movies;

SELECT director FROM movies;

SELECT title, director FROM movies;

SELECT title, year FROM movies;

SELECT * FROM movies;
#2.Задания
1.Find the movie with a row id of 6
2.Find the movies released in the years between 2000 and 2010
3.Find the movies not released in the years between 2000 and 2010
4.Find the first 5 Pixar movies and their release year
#Решения
SELECT id, title FROM movies 
WHERE id = 6;

SELECT title, year FROM movies
WHERE year BETWEEN 2000 AND 2010;

SELECT title, year FROM movies
WHERE year < 2000 OR year > 2010;

SELECT title, year FROM movies
ORDER BY id
LIMIT 5;

#3.Задания 
1.Find all the Toy Story movies
2.Find all the movies directed by John Lasseter
3.Find all the movies (and director) not directed by John Lasseter
4.Find all the WALL-* movies
#Решение
SELECT * FROM movies
WHERE title LIKE 'Toy Story%';

SELECT * FROM movies
WHERE director = 'John Lasseter';

SELECT title, director FROM movies
WHERE director <> 'John Lasseter';

SELECT * FROM movies
WHERE title LIKE 'WALL-%';

4.Задание 
1.List all directors of Pixar movies (alphabetically), without duplicates
2.List the last four Pixar movies released (ordered from most recent to least)
3.List the first five Pixar movies sorted alphabetically
4.List the next five Pixar movies sorted alphabetically
Решения

SELECT DISTINCT director
FROM movies
ORDER BY director;

SELECT title, year
FROM movies
ORDER BY year DESC
LIMIT 4;

SELECT title
FROM movies
ORDER BY title
LIMIT 5;

SELECT title
FROM movies
ORDER BY title
LIMIT 5 OFFSET 5;
5.Задания
1.List all the Canadian cities and their populations
2.Order all the cities in the United States by their latitude from north to south
3.List all the cities west of Chicago, ordered from west to east
4.List the two largest cities in Mexico (by population)
5.List the third and fourth largest cities (by population) in the United States and their population

CREATE TABLE north_american_cities (
    city TEXT,
    country TEXT,
    population INTEGER,
    latitude REAL,
    longitude REAL
);
INSERT INTO north_american_cities (city, country, population, latitude, longitude) VALUES
('Guadalajara', 'Mexico', 1500800, 20.659699, -103.349609),
('Toronto', 'Canada', 2795060, 43.653226, -79.383184),
('Houston', 'United States', 2195914, 29.760427, -95.369803),
('New York', 'United States', 8405837, 40.712784, -74.005941),
('Philadelphia', 'United States', 1553165, 39.952584, -75.165222),
('Havana', 'Cuba', 2106146, 23.05407, -82.345189),
('Mexico City', 'Mexico', 8555500, 19.432608, -99.133208),
('Phoenix', 'United States', 1513367, 33.448377, -112.074037),
('Los Angeles', 'United States', 3884307, 34.052234, -118.243685),
('Ecatepec de Morelos', 'Mexico', 1742000, 19.601841, -99.050674),
('Montreal', 'Canada', 1717767, 45.501689, -73.567256),
('Chicago', 'United States', 2718782, 41.878114, -87.629798);

SELECT city, population
FROM north_american_cities
WHERE country = 'Canada';

SELECT city, latitude
FROM north_american_cities
WHERE country = 'United States'
ORDER BY latitude DESC;

SELECT city, longitude
FROM north_american_cities
WHERE longitude < -87.629798
ORDER BY longitude ASC;

SELECT city, population
FROM north_american_cities
WHERE country = 'Mexico'
ORDER BY population DESC
LIMIT 2;

SELECT city, population
FROM north_american_cities
WHERE country = 'United States'
ORDER BY population DESC
LIMIT 2 OFFSET 2;
