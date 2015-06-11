# Scaled-valued Function #

Scalar valued functions always return a single scalar value. This can be any data type except for `text, ntext, image, cursor, timestamp`.

Syntax:

```
-- create or alter
{CREATE|ALTER} FUNCTION fnFunctionName (
    @param1 INT,
    ...,
    @paramN NVARCHAR(20)
  )
RETURNS INT -- return data type
AS
  BEGIN
    RETURN 0 -- return value
  END

-- drop
DROP FUNCTION fnFunctionName
```

Usage:
`SELECT fnFunctionName(0, ..., 'another parameter')`

## Encryption ##

A function can be encrypted using `WITH ENCRYPTION` before the `AS` keyword.

## Schema Binding ##

A function can be schema bound by using `WITH SCHEMABINDING` before the `AS` keyword. This binds the function to database objects which is references, preventing those objects from being modified in any way which would affect the function definition.

In order to use schema binding, objects must be referenced using their two-part names, and cannot reference themselves.
