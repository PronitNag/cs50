# SQL Code Explanation

## Example 1
```sql
INSERT INTO employees
VALUES (1, "Eugene", "Krabs", 25.50, "2023-01-02");
SELECT * FROM employees;
```
### Explanation:
- **INSERT INTO employees**: Ek naya record add kar raha hai `employees` table me.
- **VALUES (1, "Eugene", "Krabs", 25.50, "2023-01-02")**:
  - `1` → Employee ID
  - `Eugene` → First Name
  - `Krabs` → Last Name
  - `25.50` → Salary
  - `2023-01-02` → Joining Date
- **SELECT * FROM employees**: Poore `employees` table ke records ko show karega.

---

## Example 2
```sql
INSERT INTO employees
VALUES  (2, "Squidward", "Tentacles", 15.00, "2023-01-03"), 
                (3, "Spongebob", "Squarepants", 12.50, "2023-01-04"), 
                (4, "Patrick", "Star", 12.50, "2023-01-05"), 
                (5, "Sandy", "Cheeks", 17.25, "2023-01-06");
SELECT * FROM employees;
```
### Explanation:
- **INSERT INTO employees**: Multiple records ek saath insert ho rahe hain.
- Har record me:
  - Employee ID
  - First Name
  - Last Name
  - Salary
  - Joining Date
- **SELECT * FROM employees**: `employees` table ke sabhi records ko show karega.

---

## Example 3
```sql
INSERT INTO employees (employee_id, first_name, last_name)
VALUES  (6, "Sheldon", "Plankton");
SELECT * FROM employees;
```
### Explanation:
- **INSERT INTO employees (employee_id, first_name, last_name)**: Sirf specific columns (`employee_id`, `first_name`, `last_name`) me data insert ho raha hai.
- **VALUES (6, "Sheldon", "Plankton")**:
  - `6` → Employee ID
  - `Sheldon` → First Name
  - `Plankton` → Last Name
- **SELECT * FROM employees**: Updated `employees` table ko display karega.

---

### Summary
- `INSERT INTO` ka use karke ek ya multiple rows insert kar sakte hain.
- Agar specific columns mention nahi kiye, toh saari columns ke liye values deni padengi.
- `SELECT * FROM employees` ka use table ke sabhi records dekhne ke liye hota hai.
