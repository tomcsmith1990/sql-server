# Default Constraint #

A default constraint is a default value for a column.

To create a default constraint on an existing column, use:

`ALTER TABLE <table_name> ADD CONSTRAINT <constraint_name> DEFAULT <default_value> FOR <column_name>`

To create a new column with a default constraint, use:

`ALTER TABLE <table_name> ADD <column_name> <column_type> CONSTRAINT <constraint_name> DEFAULT <default_value>`

To drop the default constraint, use:

`ALTER TABLE <table_name> DROP CONSTRAINT <constraint_name>`

The default value will not replace an explicit `NULL` inserted into the table.
