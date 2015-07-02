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

Unlike a scalar-valued function, the function body isn't enclosed in a `BEGIN...END`.

## Multi-statement table-valued function ##

A multi-statement table-valued function also returns a table.

Syntax:

```
{CREATE|ALTER} FUNCTION fnMSTVF()
RETURNS @Table TABLE (Id INT, Name NVARCHAR(20))
AS
  BEGIN
    INSERT INTO @Table
    SELECT Id, Name FROM tblEmployees
    RETURN
  END
```

Usage: `SELECT * FROM fnMSTVF()`

The structure of the table is defined in the function definition.

The function body is enclosed in a `BEGIN...END`.

## Comparison of inline table-valued functions and multi-statement table-valued functions ##

Inline table-valued functions give better performance than multi-statement table-valued functions because SQL Server treats the former similar to views, but treats the latter similar to stored procedures.

An inline table-valued function can be used to update the underlying table using `UPDATE fnInlineTVF() SET ...`. This is not possible with a multi-statement table-valued function.
