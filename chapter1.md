---
title: 'Chapter Title Here'
description: 'Chapter description goes here.'
free_preview: true
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

Tạo Trình kích hoạt sẽ kiểm tra bảng nhân viên cho EITHER INSERT, UPDATE hoặc
XÓA. Đó là lựa chọn của bạn để chọn và bạn chỉ cần làm một. Kích hoạt sẽ
chèn một bản ghi để kiểm toán bảng cho mỗi thay đổi cột.


`@instructions`
Nếu một hàng được CHỨNG MINH, Old_Value phải là NULL. Nếu một hàng là DELETEd, New_Value sẽ là
VÔ GIÁ TRỊ.
DateCreated phải là ngày và giờ hệ thống hiện tại.
Sử dụng chức năng hệ thống CURRENT_USER để lấy tên của người dùng đang chạy truy vấn cho cột
Được tạo bởi.

`@hint`


`@pre_exercise_code`
```{python}

```

`@sample_code`
```{python}

```

`@solution`
```{python}
CREATE TABLE audit 
(  AuditID INT identity(1,1) NOT NULL PRIMARY KEY,  -- AuditID as integer.  It should automatically assign the value starting with 1 and incrementing by 1.  TableName VARCHAR(10) NOT NULL,  -- TableName as VARCHAR(10).  It cannot have NULLs.  ActionTaken CHAR(6) NOT NULL, -- ActionTaken as CHAR(6).  It cannot have NULLs.  ColumnName VARCHAR(12) NOT NULL,  -- ColumnName as VARCHAR(12).  It cannot have NULLs.  Old_Value VARCHAR(255), -- Old_Value as VARCHAR(255).  New_Value VARCHAR(255), -- New_Value as VARCHAR(255).  DateCreated SMALLDATETIME NOT NULL DEFAULT GETDATE(),  -- DateCreated as SMALLDATETIME.  It cannot have NULLs.  CreatedBy VARCHAR(255) NOT NULL  -- User as VARCHAR(255).  It cannot have NULLs.  ) --------------------------------------------------------------------- --DROP TRIGGER trg_audit_employee --------------------------------------------------------------------- TẠO TRIGGER trg_audit_employee TRÊN nhân viên SAU KHI XÁC NHẬN, CẬP NHẬT, XÓA NHƯ THIẾT LẬP TÀI KHOẢN TRÊN NỀN TẢNG @old_emp_no int = NULL old_salary money = NULL DECLARE @new_emp_no int = NULL DECLARE @new_emp_fname char (20) = NULL, @new_emp_lname char (20) = NULL DECLARE @new_dept_no char (4) = NULL DECLARE @user VARCHAR (255) = '' SELECT @user = CURRENT_USER SELECT @new_emp_no = emp_no TỪ đã chèn
 
IF @new_emp_no LÀ NULL SET @Action = 'XÓA' ELSE BEGIN CHỌN @old_emp_no = emp_no TỪ đã xóa IF @old_emp_no LÀ NULL SET @Action = 'INSERT' ELSE SET @Action = 'CẬP NHẬT' , 'CẬP NHẬT') CHỌN @old_emp_no = emp_no, @old_emp_fname = emp_fname, @old_emp_lname = emp_lname, @old_dept_no = dept_no, @old_salary = mức lương đã bị xóa IF @Action , @new_emp_fname = emp_fname, @new_emp_lname = emp_lname, @new_dept_no = dept_no, @new_salary = Lương
 TỪ chèn ------------------------------------------------ -----------------------
 
NẾU CẬP NHẬT (emp_no) INSERT INTO kiểm toán (TableName, ActionTaken, ColumnName, Old_Value, New_Value, createdBy) VALUES ('worker', @Action, 'emp_no', @old_emp_no, @new_emp_no kiểm toán (TableName, ActionTaken, ColumnName, Old_Value, New_Value, createdBy) VALUES ('staff', @Action, 'emp_fname', @old_emp_fname, @new_emp_fname, @user) NẾU CẬP NHẬT , Old_Value, New_Value, createdBy) VALUES ('staff', @Action, 'emp_lname', @old_emp_lname, @new_emp_lname, @user) NẾU CẬP NHẬT (dept_no) INSERT INTO kiểm toán (TableName VALUES ('staff', @Action, 'dept_no', @old_dept_no, @new_dept_no, @user) NẾU CẬP NHẬT (tiền lương) Kiểm tra INTO (TableName, ActionTaken, CộtName, Old_Value, New_Value, createdBy Hành động, 'tiền lương', @old_salary, @new_salary, @user)
 
-------------------------------------------------- --------------------- NẾU @Action = 'XÓA' BEGIN CHỈ VÀO kiểm toán (TableName, ActionTaken, CộtName, Old_Value, New_Value, createdBy) VALUES ('staff' , @Action, 'emp_no', @old_emp_no, @new_emp_no, @user) XÁC NHẬN kiểm toán (TableName, ActionTaken, CộtName, Old_Value, New_Value, createdBy) VALUES ('worker', @Action, ' new_emp_fname, @user) Kiểm tra INSERT INTO (TableName, ActionTaken, ColumnName, Old_Value, New_Value, createdBy) VALUES ('worker', @Action, 'emp_lname', @old_emp_lname, @new_emp_l , ColumnName, Old_Value, New_Value, createdBy) VALUES ('staff', @Action, 'dept_no', @old_dept_no, @new_dept_no, @user) INSERT INTO kiểm toán (TableName, ActionTaken, ColumnName, Old_Val nhân viên ', @Action,' lương ', @old_salary, @new_salary, @user) END THIẾT LẬP TÀI KHOẢN ----------------------------------------------- ------------------------ XÁC NHẬN GIÁ TRỊ nhân viên (2200, 'Murphy', 'Williams', 'd3', NULL) CẬP NHẬT nhân viên SET emp_fname = 'Oliver', emp_lname = 'Whalen' WHERE emp_no = 2200
CẬP NHẬT nhân viên SET lương = 50000 WHERE emp_no = 2200 nhân viên XÓA XÓA WHERE emp_no = 2200 CHỌN * TỪ kiểm toán TRUNCATE BẢNG
```

`@sct`
```{python}

```
