---
title: 'Chapter Title Here'
description: 'Chapter description goes here.'
---

## Example coding exercise

```yaml
type: NormalExercise
key: e8c1edbe67
lang: python
xp: 100
skills: 2
```

This is an example exercise.

`@instructions`


`@hint`


`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}

```

`@solution`
```{python}

```

`@sct`
```{python}

```

---

## SQL exercise

```yaml
type: NormalExercise
key: 69a24d24cd
xp: 100
```

CREATE TABLE audit for sql server programming CREATE TABLE audit for sql server programming CREATE TABLE audit for sql server programming CREATE TABLE audit for sql server programming CREATE TABLE audit for sql server programming

`@instructions`


`@hint`


`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}
CREATE TRIGGER trg_audit_employee ON employee  AFTER INSERT, UPDATE, DELETE AS SET NOCOUNT ON DECLARE @old_emp_no int = NULL DECLARE @old_emp_fname char(20) = NULL, @old_emp_lname char(20) = NULL DECLARE @old_dept_no char(4) = NULL, @old_salary money = NULL DECLARE @new_emp_no int = NULL DECLARE @new_emp_fname char(20) = NULL, @new_emp_lname char(20) = NULL DECLARE @new_dept_no char(4) = NULL, @new_salary money = NULL DECLARE @Action CHAR(6) DECLARE @user VARCHAR(255) = '' SELECT @user = CURRENT_USER SELECT @new_emp_no = emp_no FROM inserted 
 
IF @new_emp_no IS NULL SET @Action = 'DELETE' ELSE  BEGIN  SELECT @old_emp_no = emp_no FROM deleted  IF @old_emp_no IS NULL SET @Action = 'INSERT'  ELSE SET @Action = 'UPDATE' END IF @Action IN ('DELETE', 'UPDATE')  SELECT @old_emp_no = emp_no,    @old_emp_fname = emp_fname,    @old_emp_lname = emp_lname,    @old_dept_no = dept_no,    @old_salary = salary  FROM deleted IF @Action IN ('INSERT', 'UPDATE')  SELECT @new_emp_no = emp_no,    @new_emp_fname = emp_fname,    @new_emp_lname = emp_lname,    @new_dept_no = dept_no,    @new_salary = salary 
 FROM inserted ----------------------------------------------------------------------- 
 
IF UPDATE(emp_no) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_no',      @old_emp_no, @new_emp_no, @user) IF UPDATE(emp_fname) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_fname',      @old_emp_fname, @new_emp_fname, @user) IF UPDATE(emp_lname) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_lname',      @old_emp_lname, @new_emp_lname, @user) IF UPDATE(dept_no) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'dept_no',      @old_dept_no, @new_dept_no, @user) IF UPDATE(salary) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'salary',      @old_salary, @new_salary, @user) 
 
-----------------------------------------------------------------------      IF @Action = 'DELETE' BEGIN INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_no',      @old_emp_no, @new_emp_no, @user) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_fname',      @old_emp_fname, @new_emp_fname, @user) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'emp_lname',      @old_emp_lname, @new_emp_lname, @user) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'dept_no',      @old_dept_no, @new_dept_no, @user) INSERT INTO audit (TableName, ActionTaken, ColumnName,       Old_Value, New_Value, CreatedBy)    VALUES ('employee', @Action, 'salary',      @old_salary, @new_salary, @user) END SET NOCOUNT OFF ----------------------------------------------------------------------- INSERT INTO employee VALUES (2200,'Murphy','Williams','d3',NULL) UPDATE employee SET emp_fname = 'Oliver', emp_lname = 'Whalen' WHERE emp_no = 2200 
UPDATE employee SET salary = 50000 WHERE emp_no = 2200 DELETE employee WHERE emp_no = 2200 SELECT * FROM audit TRUNCATE TABLE audit 
 
```

`@solution`
```{python}
CREATE TABLE audit 
(  AuditID INT identity(1,1) NOT NULL PRIMARY KEY,  -- AuditID as integer.  It should automatically assign the value starting with 1 and incrementing by 1.  TableName VARCHAR(10) NOT NULL,  -- TableName as VARCHAR(10).  It cannot have NULLs.  ActionTaken CHAR(6) NOT NULL, -- ActionTaken as CHAR(6).  It cannot have NULLs.  ColumnName VARCHAR(12) NOT NULL,  -- ColumnName as VARCHAR(12).  It cannot have NULLs.  Old_Value VARCHAR(255), -- Old_Value as VARCHAR(255).  New_Value VARCHAR(255), -- New_Value as VARCHAR(255).  DateCreated SMALLDATETIME NOT NULL DEFAULT GETDATE(),  -- DateCreated as SMALLDATETIME.  It cannot have NULLs.  CreatedBy VARCHAR(255) NOT NULL  -- User as VARCHAR(255).  It cannot have NULLs.  ) --------------------------------------------------------------------- --DROP TRIGGER trg_audit_employee --------------------------------------------------------------------- 
```

`@sct`
```{python}

```
