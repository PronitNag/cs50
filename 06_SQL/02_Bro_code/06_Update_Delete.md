-- Ye query employees table ko update, retrieve aur delete kar rahi hai.

-- Step 1: Employee ka hourly_pay update karna
UPDATE employees
SET hourly_pay = 10.25
WHERE employee_id = 6;

-- Step 2: Pura employees table dikhana taaki update ka effect check ho sake
SELECT * FROM employees;

-- Step 3: Employee ko delete karna jiska employee_id 6 hai
DELETE FROM employees
WHERE employee_id = 6;

-- Step 4: Pura employees table dikhana taaki delete ka effect check ho sake
SELECT * FROM employees;

