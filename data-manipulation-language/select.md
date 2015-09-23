# Querying tables using `SELECT` #

The `SELECT` statement is used to get data from tables.

The general form of the statement is:

```
SELECT  <column_list>
FROM    <table_name>
WHERE   <condition>
```

The `WHERE` clause is optional, and will filter the results by row. Omitting the `WHERE` clause will return a value for each row.

For example, to select the names of customers living in Cambridge from a table of addresses:

```
SELECT  [name]
FROM    [tblCustomers]
WHERE   [city] = 'Cambridge'
```

To select all of the columns from a table a `*` may be used in place of `<column_list>`:

```
SELECT  *
FROM    [tblCustomers]
```

However, this offers worse performance.
