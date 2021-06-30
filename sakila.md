# SAKILA
1. **List all actors.**
    ```sql
    USE sakila;
    SELECT CONCAT(first_name, " ", last_name) as full_name FROM actor;
    ```

2. **Find the surname of the actor with the forename 'John'.**
    ```sql
    USE sakila;
    SELECT last_name FROM actor
    WHERE first_name = 'John';
    ```

3. **Find all actors with surname 'Neeson'.**
    ```sql
    USE sakila;
    SELECT CONCAT(first_name, " ", last_name) as Name
    FROM actor
    WHERE last_name = 'Neeson';
    ```

4. **Find all actors with ID numbers divisible by 10.**
    ```sql
    USE sakila;
    SELECT actor_id, CONCAT(first_name, " ", last_name) as Name
    FROM actor
    WHERE actor_id % 10 = 0;
    ```

5. **What is the description of the movie with an ID of 100?**
    ```sql
    USE sakila;
    SELECT description FROM film
    WHERE film_id = 100;
    ```

6. **Find every R-rated movie.**
    ```sql
    USE sakila;
    SELECT title FROM film
    WHERE rating = 'R';
    ```

7. **Find every non-R-rated movie.**
    ```sql
    USE sakila;
    SELECT title FROM film
    WHERE rating != 'R';
    ```

8. **Find the ten shortest movies.**
    ```sql
    USE sakila;
    SELECT title FROM film
    ORDER BY length ASC
    LIMIT 10;
    ```

9. **Find the movies with the longest runtime, without using LIMIT.**
    ```sql
    USE sakila;
    SELECT title FROM  film
    WHERE length = (
        SELECT MAX(length) FROM film);
    ```

10. **Find all movies that have deleted scenes.**
    ```sql
    USE sakila;
    SELECT * FROM film
    WHERE special_features LIKE "%Deleted Scenes%";
    ```

11. **Using HAVING, reverse-alphabetically list the last names that are not repeated.**
    ```sql
    USE sakila;
    SELECT last_name FROM actor
    GROUP BY last_name
    HAVING COUNT(last_name) = 1
    ORDER BY last_name DESC;
    ```

12. **Using HAVING, list the last names that appear more than once, from highest to lowest frequency.**
    ```sql
    USE sakila;
    SELECT last_name, COUNT(last_name)as frequency FROM actor
    GROUP BY last_name
    HAVING COUNT(last_name) > 1
    ORDER BY COUNT(last_name) DESC
    ;
    ```

13. **Which actor has appeared in the most films?**
    ```sql
    USE sakila;
    SELECT COUNT(film_actor.actor_id), first_name, last_name
    FROM film_actor
    JOIN actor ON film_actor.actor_id = actor.actor_id
    WHERE film_actor.actor_id = (
     SELECT actor_id FROM actor WHERE actor_id = film_actor.actor_id
    )
    GROUP BY film_actor.actor_id
    ORDER BY COUNT(film_actor.actor_id) DESC
    LIMIT 1;
    ```

14. **When is 'Academy Dinosaur' due?**
    ```sql
    ```

15. **What is the average runtime of all films?**
    ```sql
    USE sakila;
    SELECT AVG(length) AS average_length
    FROM  film
    ;
    ```

16. **List the average runtime for every film category.**
    ```sql
    USE sakila;
    SELECT ANY_VALUE(category.name) as category_name,
    ANY_VALUE(AVG(film.length)) AS avg_length
    FROM category
    JOIN film_category
    ON category.category_id = film_category.category_id
    JOIN film
    ON film_category.film_id = film.film_id
    GROUP BY category.name;
    ```

17. **List all movies featuring a robot.**
    ```sql
    ```

18. **How many movies were released in 2010?**
    ```sql
    ```

19. **Find the titles of all the horror movies.**
    ```sql
    ```

20. **List the full name of the staff member with the ID of 2.**
    ```sql
    ```

21. **List all the movies that Fred Costner has appeared in.**
    ```sql
    ```

22. **How many distinct countries are there?**
    ```sql
    ```

23. **List the name of every language in reverse-alphabetical order.**
    ```sql
    ```

24. **List the full names of every actor whose surname ends with '-son' in alphabetical order by their forename.**
    ```sql
    ```

25. **Which category contains the most films?**
    ```sql
    ```