# sql-portfolio
SQL practice queries and business case challenges
## Challenge 1: First 8 Paying Customers
### Business Problem
We want to reward our first 8 paying customers.
### SQL Query

```sql
SELECT customer_id
FROM payment
ORDER BY payment_date ASC
LIMIT 10;
```
### Explanation

- `SELECT customer_id` retrieves customer IDs
- `FROM payment` selects data from the payment table
- `ORDER BY payment_date ASC` sorts from earliest payment to latest
- `LIMIT 8` returns only the first 10 customers

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
