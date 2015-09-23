# Temporary Tables #

Temporary tables are created in `tempdb` and are automatically dropped when they are no longer needed.

There are two types of temporary table - local and global.

## Local temporary tables ##

A local temporary table is only available to the connection which created it and is automatically dropped when the connection which created it is closed.

To create a local temporary table, prefix the name with `#`:

`CREATE TABLE #tblPersonDetails (id INT, name VARCHAR(64)`

When a local temporary table is created within a stored procedure, it will be dropped when execution of the stored procedure completes.

The name of a local temporary table does not have to be unique across connections. Multiple connections may create a local temporary table with the same name.

## Global temporary tables ##

A global temporary table is visible to all connections and is automatically dropped when the last connection which references that table is closed.

To create a global temporary table, prefix the name with `##`:

`CREATE TABLE ##tblEmployeeDetails (id INT, name VARCHAR(64)`

The name of a global temporary table must be unique.

## Finding a temporary table ##

SQL Server appends some random characters to the name of the temporary table, so querying `sys.objects` for the table name may not work. Instead, use `SELECT name FROM tempdb.sys.objects WHERE name LIKE '#tblPersonDetails%'`.

Alternatively, look for the table in `tempdb`.

## Manually dropping temporary tables ##

Temporary tables can be explicitly dropped in the same way as a normal table:

`DROP TABLE #tblLocalTemporaryTable` or `DROP TABLE ##tblGlobalTemporaryTable`
