```sql
-- Create Table
CREATE TABLE employees (
    employee_id int PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50), 
    hourly_pay DECIMAL(5, 2),
    hire_date DATE
);

-- Rename Table
RENAME TABLE employees TO workers;

-- Drop Table
DROP TABLE employees;

-- Add Column
ALTER TABLE employees ADD phone_number VARCHAR(15);

-- Rename Column
ALTER TABLE employees RENAME COLUMN phone_number TO email;

-- Modify Column Type
ALTER TABLE employees MODIFY COLUMN email VARCHAR(15);

-- Change Column Position
ALTER TABLE employees MODIFY email VARCHAR(100) AFTER last_name;

-- Move Column to First Position
ALTER TABLE employees MODIFY email VARCHAR(100) FIRST;

-- Drop Column
ALTER TABLE employees DROP COLUMN email;

-- ⚠ Issues:
-- 1. After DROP TABLE, employees no longer exists.
-- 2. After RENAME TABLE, changes should be made to 'workers'.
-- 3. Correct sequence is required to avoid errors.
```
