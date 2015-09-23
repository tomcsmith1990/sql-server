# Unique Constraint #

A unique constraint ensures that values in a column are unique (i.e. there are no duplicate values).

To add a unique constraint, use:

`ALTER TABLE <table_name> ADD CONSTRAINT <constraint_name> UNIQUE(<column_name>)`

Whereas a table can only have one primary key, it can have many unique constraints. This means that uniqueness can be enforced on a column which is not part of the primary key.

A primary key does not allow any `NULL` values, but a unique constraint will allow one `NULL`.

The convention for naming is `UQ_`, for example `UQ_constraint1`.
