# Indexes #

Indexes are used to:

- maintain data integrity
- speed up queries

There are many types of indexes:

- primary keys
- foreign keys
- unique indexes
- XML indexes
  - primary XML indexes
  - secondary XML indexes
  - selective XML indexes
  - secondary selective XML indexes
- full-text indexes
- spatial indexes

Some indexes can either be `CLUSTERED` or `NONCLUSTERED`. A clustered index determines the physical order which data is stored in, therefore a table can only have one clustered index.

If all of the columns in a `SELECT` clause are present in a single index, the query is called a _covering query_. In this case there is no need to look up data in the table, data can be returned directly from the index. A clustered index always covers a query, since the index contains all of the data in the table.

Indexes have some disadvantages:

- non-clustered indexes require additional disk space which grows with the table size
- DML statements (`INSERT|UPDATE|DELETE`) can become slow because indexes need to be updated*

[*] this means that indexes can be good when data is mostly read, but can become slow when data is mostly written. (_This may be a fact which I've just made up_)
