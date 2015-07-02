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

Imagine the following scenario:

We have two tables:

```
CREATE TABLE tblDepartment
    (
      DepartmentId INT PRIMARY KEY ,
      DepartmentName VARCHAR(20)
    );

CREATE TABLE tblEmployee
    (
      Id INT ,
      Name VARCHAR(20) ,
      DepartmentId INT
        FOREIGN KEY REFERENCES dbo.tblDepartment ( DepartmentId )
    );
```

We also have a view which joins these two tables:

```
CREATE VIEW vwEmployeesAndDepartment
AS
    SELECT  Id ,
            Name ,
            DepartmentName
    FROM    tblEmployee
            INNER JOIN tblDepartment ON tblEmployee.DepartmentId = tblDepartment.DepartmentId;
```

`tblEmployee` has the row `(3, 'SomeEmployee', 2)` and `tblDepartment` has the rows `(1, 'HR'), (2, 'Development')`.

When we run `UPDATE vwEmployeesAndDepartment SET DepartmentName = 'HR' WHERE Id = 3`, SQL Server will actually update the row in `tblDepartment` to be `(2, 'HR')`.

This is clearly wrong. We actually wanted to change the row in `tblEmployee` to be `(3, 'SomeEmployee', 1)`. An instead of trigger can do this for us:

```
CREATE TRIGGER tr_vwEmployeesAndDepartment_InsteadOfUpdate
ON vwEmployeesAndDepartment
INSTEAD OF UPDATE
AS
	BEGIN
		DECLARE @deptName VARCHAR(20);
		SET @deptName = (SELECT DepartmentName FROM inserted);

		DECLARE @deptId INT;
		SET @deptId = (SELECT DepartmentId FROM dbo.tblDepartment WHERE DepartmentName = @deptName);

		DECLARE @employeeId INT;
		SET @employeeId = (SELECT Id FROM inserted);

		UPDATE dbo.tblEmployee SET DepartmentId = @deptId WHERE Id = @employeeId;
	END
```
