# SQL queries and business case challenges


## Challenge 1

### Business Problem
We want to reward our first 8 paying customers. We need to find their customer IDs.

---

### SQL Query

```sql
SELECT customer_id
FROM payment
ORDER BY payment_date ASC
LIMIT 8;
```

---

### Explanation

- `SELECT customer_id` retrieves customer IDs  
- `FROM payment` selects data from the payment table  
- `ORDER BY payment_date ASC` sorts from earliest to latest payment  
- `LIMIT 8` returns only the first 8 customers  


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


## Challenge 4

### Business Problem
We have two staff members, with Staff IDs 1 and 2. We want to give a bonus to the staff member that handled the most payments. (Most in terms of number of payments processed, not total dollar amount).
How many payments did each staff member handle and who gets the bonus?

---

### SQL Query

```sql
SELECT staff_id, COUNT(amount) FROM payment
GROUP BY staff_id
ORDER BY COUNT(amount) DESC
LIMIT 1;
```

---

### Explanation

- `SELECT staff_id, COUNT(amount)` returns each staff member's ID and the number of payments they processed
- `FROM payment` selects data from the payment table
- `GROUP BY staff_id` groups the payments by each staff member
- `COUNT(amount)` counts the number of payments for each staff member
- `ORDER BY COUNT(amount) DESC` sorts the results from the highest payment count to the lowest
- `LIMIT 1` returns only the staff member with the highest number of payments


## Challenge 5

### Business Problem

We are launching a platinum service for our most loyal customers. We will assign Platinum status to customers who have made **40 or more payment transactions**.
Which customer IDs are eligible for Platinum status?

---

### SQL Query

```sql
SELECT customer_id, COUNT(amount)
FROM payment
GROUP BY customer_id
HAVING COUNT(amount) >= 40;
```

---

### Explanation

- `SELECT customer_id, COUNT(amount)` returns each customer's ID and the number of payment transactions they made
- `FROM payment` selects data from the payment table
- `GROUP BY customer_id` groups the payments by each customer
- `COUNT(amount)` counts the number of payments made by each customer
- `HAVING COUNT(amount) >= 40` filters the results to include only customers with 40 or more payment transactions


## Challenge 6

### Business Problem

The marketing team wants to identify high-value customers who have spent **more than $110** with **Staff Member #2**. These customers may qualify for a special loyalty reward or exclusive promotion.

---

### SQL Query

```sql
SELECT customer_id, SUM(amount)
FROM payment
WHERE staff_id = 2
GROUP BY customer_id
HAVING SUM(amount) > 110;
```

---

### Explanation

- `SELECT customer_id, SUM(amount)` returns each customer's ID and the total amount they spent.
- `FROM payment` retrieves payment records.
- `WHERE staff_id = 2` includes only payments processed by Staff Member #2.
- `GROUP BY customer_id` groups the payments by customer.
- `SUM(amount)` calculates the total amount spent by each customer.
- `HAVING SUM(amount) > 110` filters the results to include only customers who spent more than **$110**.


## Challenge 7

### Business Problem

The customer service team needs to locate the customer with the **highest customer ID** whose **first name begins with "E"** and whose **address ID is less than 500**.

---

### SQL Query

```sql
SELECT first_name, last_name
FROM customer
WHERE first_name LIKE 'E%'
AND address_id < 500
ORDER BY customer_id DESC
LIMIT 1;
```

---

### Explanation

- `SELECT first_name, last_name` returns the customer's first and last name.
- `FROM customer` retrieves data from the customer table.
- `WHERE first_name LIKE 'E%'` filters customers whose first name starts with **E**.
- `AND address_id < 500` limits the results to customers with an address ID below **500**.
- `ORDER BY customer_id DESC` sorts the matching customers by customer ID in descending order.
- `LIMIT 1` returns only the customer with the highest customer ID.


