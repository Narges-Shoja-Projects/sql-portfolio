# SQL queries and business case challenges

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
