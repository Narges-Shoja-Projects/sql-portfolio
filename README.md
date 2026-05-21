# SQL queries and business case challenges

## Challenge 1
### Business Problem
We want to reward our first 8 paying customers. We need to find their customer IDs.
### SQL Query

```sql
SELECT customer_id
FROM payment
ORDER BY payment_date ASC
LIMIT 8;
```
### Explanation

- `SELECT customer_id` retrieves customer IDs
- `FROM payment` selects data from the payment table
- `ORDER BY payment_date ASC` sorts from earliest payment to latest
- `LIMIT 8` returns only the first 8 customers

### Result

| customer_id |
|-------------| 
| 416 |
| 516 |
| 239 |
| 592 |
| 49 |
| 264 |
| 46 |
| 481 |


## Challenge 2

### Business Problem
A customer wants to quickly rent a movie during a short break. We need to find the shortest movies available.

---

### SQL Query

```sql
SELECT title, length
FROM film
ORDER BY length ASC
LIMIT 5;
```

---

### Explanation

- `SELECT title, length` retrieves movie titles and their duration  
- `FROM film` selects data from the film table  
- `ORDER BY length ASC` sorts movies from shortest to longest  
- `LIMIT 5` returns only the 5 shortest movies  

---

### Result

| title | length |
|------|--------|
| Labyrinth League | 46 |
| Alien Center | 46 |
| Iron Moon | 46 |
| Kwai Homeward | 46 |
| Ridgemont Submarine | 46 |


## Challenge 3

### Business Problem
We want to know how many movies a customer can watch if she only watches movies that are 50 minutes or less in runtime.

---

### SQL Query

```sql
SELECT COUNT(title)
FROM film
WHERE length <= 50;
```

---

### Explanation

- `SELECT COUNT(title)` counts the number of movies  
- `FROM film` selects data from the film table  
- `WHERE length <= 50` filters movies that are 50 minutes or less  

---

### Result

| count |
|------|
| 37 |
