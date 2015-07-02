# Table-valued Function #

## Inline table-valued function ##

An inline table-valued function returns a table.

Syntax:

```
-- create or alter
{CREATE|ALTER} FUNCTION fnFunctionName (
    @param1 INT,
    ...,
    @paramN NVARCHAR(20)
  )
RETURNS TABLE
AS
  RETURN (SELECT * FROM tblSomeTable) -- any SELECT statement, can use function parameters

-- drop
DROP FUNCTION fnFunctionName
```

Usage: `SELECT * FROM fnFunctionName(0, ..., 'another parameter')`

The structure of the table is determined by the `SELECT` statement in the function.

An inline table-valued function can be used to achieve the functionality of parameterized views.

Unlike a scalar-valued function, the function definition isn't enclosed in a `BEGIN...END`.
