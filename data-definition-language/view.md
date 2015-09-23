# View #

A view is a saved SQL query, and acts like a "virtual table".

Syntax:

```
-- create or alter
{CREATE|ALTER} VIEW vwViewName
AS
  SELECT * FROM tblSomeTable

-- drop
DROP VIEW vwViewName
```

Usage: `SELECT * FROM vwViewName`

## Advantages of views ##

- can be used to hide the complexity of a database schema (e.g. tables can be normalized, but a view can provide the necessary `JOINS` to display data)
- can be used to implement row and column level security by granting `SELECT` permissions to a user for the view but not the underlying tables
  - row level security by using a `WHERE` clause
  - column level security by only including certain columns in the `SELECT` statement
- can be used to present aggregated data and hide the more detailed data

## Disadvantages of views ##

- cannot pass parameters to a view - use a table-valued function for this
- rules and defaults cannot be associated with views
- the `ORDER BY` clause is invalid in a view, unless `TOP` or `FOR XML` are also specified
- a view cannot be based on a temporary table
