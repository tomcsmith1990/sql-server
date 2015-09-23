# Querying tables using `SELECT` #

The `SELECT` statement is used to get data from tables.

The general form of the statement is:

```
SELECT  <column_list>
FROM    <table_name>
WHERE   <condition>
```

For example, to select the names of customers living in Cambridge from a table of addresses:

```
SELECT  [name]
FROM    [tblCustomers]
WHERE   [city] = 'Cambridge'
```
