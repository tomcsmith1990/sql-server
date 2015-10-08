# Combining result sets using `UNION` #

The `UNION` statement is used to combine the result sets of two or more `SELECT` statements:

```
SELECT * FROM tblIndiaCustomers
UNION
SELECT * FROM tblEuropeCustomers
```
The `SELECT` queries must return the same number of columns, and the types of each column must be equal and in the same order in each query.

`UNION ALL` can be used in the same way as `UNION`. `UNION ALL` does not remove duplicate results, but `UNION` does remove duplicates. In order to remove duplicates, `UNION` has to sort the results so is slower than `UNION ALL`.

To order the results, an `ORDER BY` statement can be used after the final `SELECT` query.

## Difference between `UNION` and `JOIN` ##

A `UNION` combines the results of two or more queries into a single result set. It can be used to combine rows from two or more tables.

A `JOIN` combines data from two or more tables based on a logical relationship between those tables. It can be used to combine columns from two or more tables.
