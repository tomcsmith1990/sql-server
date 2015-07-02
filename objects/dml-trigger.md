# DML Trigger #

DML (data manipulation language) triggers are fired automatically on DML events (`INSERT|UPDATE|DELETE`).

DML triggers can be created on tables or views.

DML triggers are classified into two types:

- `AFTER` (or `FOR`) triggers, which fire after the DML event
- `INSTEAD OF` triggers, which fire instead of the DML event

Special tables can be used within the trigger body to get the values used in the event:

- the `inserted` table contains the inserted data
- the `deleted` table contains the deleted data

In an `UPDATE` event, `inserted` will contain the new data and `deleted` will contain the old data.

## After triggers ##

Syntax:

```
CREATE TRIGGER tr_tblName_For{Insert|Update|Delete}
ON tblName
FOR {INSERT|UPDATE|DELETE}
AS
  BEGIN
    ...
  END
```

An after trigger may be used for auditing, for example when a `DELETE` event happens, we may copy the deleted data to an audit table, along with details on who made the change and when.

## Instead of trigger ##

Syntax:

```
CREATE TRIGGER tr_tblName_InsteadOf{Insert|Update|Delete}
ON tblName
INSTEAD OF {INSERT|UPDATE|DELETE}
AS
  BEGIN
    ...
  END
```

An instead of trigger is useful for modifying the data in underlying tables of a view. If a view joins two or more tables, then we can't directly modify data in the view.
