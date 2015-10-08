# The `COALESCE` function #

The `COALESCE` function returns the first `NOT NULL` value from its arguments.

For example, with the table `tblCustomers`:

|FirstName|MiddleName|LastName|
|-|-|-|
|NULL|NULL|Jones|
|Adam|NULL|Smith|

The query:

```
SELECT COALESCE(FirstName, MiddleName, LastName) AS Name
FROM tblCustomers
```

would return the following result set:

|Name|
|-|
|Jones|
|Adam|
