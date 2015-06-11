# Stored Procedure #

A stored procedure is a group of T-SQL statements, which allows the same query to easily be executed again and again.

## Creation ##
Syntax:
```
CREATE {PROCEDURE|PROC} spMyStoredProcedure
AS
  BEGIN
    -- some sql code
  END
```

## Execution ##
To execute a stored procedure named `spMyStoredProcedure`, run:

`spMyStoredProcedure` or `EXEC spMyStoredProcedure` or `EXECUTE spMyStoredProcedure`

Naming convention: don't begin a stored procedure name with `sp_`. System stored procedures use this convention, and a future one could have the same name as your procedure.

## Parameters ##
Stored procedures can also have parameters:
```
CREATE PROCEDURE spMyStoredProcedure
  @param1 NVARCHAR(20),
  @param2 INT
AS
  BEGIN
    -- some sql code
  END
```

To execute a stored procedure, run it with comma separated values (parameter name can optionally be specified, allow parameters to be given in any order):

`spMyStoredProcedure 'param1', 0` or `spMyStoredProcedure @param2 = 0, @param1 = 'param1'`

`EXEC` and `EXECUTE` can still be used here.

## sp_helptext ##
To view the text of a stored procedure, use the system stored procedure `sp_helptext`, i.e. `EXECUTE sp_helptext spMyStoredProcedure`.

## Encryption ##
The text of a stored procedure can be encrypted, using the `WITH ENCRYPTION` option:

```
CREATE PROCEDURE spMyStoredProcedure
WITH ENCRYPTION
AS
  ...
```

## Output Parameters ##
Output parameters are similar to `out` parameters in C#. A value is set in a stored procedure, and can then be used outside of that procedure.

```
CREATE PROCEDURE spOutputInt
  @OutputInt INT {OUTPUT|OUT}
AS
  BEGIN
    SELECT @OutputInt = 1
  END
```

To execute a stored procedure with an output parameter (and select it), use:

```
DECLARE @anOutputParameter INT
EXECUTE spOutputInt @anOutputParameter OUTPUT
SELECT @anOutputParameter
```

If the `OUTPUT` keyword is used when executing, the value returned will be `NULL`.
