# Check Constraint #

A check constraint is used to limit the range of values which can be entered for a column.

To add a check constraint, use:

`ALTER TABLE <table_name> ADD CONSTRAINT <constraint_name> CHECK <boolean_expression>`

The boolean expression can refer to column names, for example `CHECK ([Age] > 0)`. If the boolean expression returns true, then the row is inserted. If the boolean expression returns false then an error is raised.

`NULL` can be inserted into rows covered by a check constraint, because the expression returns unknown rather than false.

A new check constraint cannot be added if existing rows would fail that constraint.

To drop a check constraint, use:

`ALTER TABLE <table_name> DROP CONSTRAINT <constraint_name>`
