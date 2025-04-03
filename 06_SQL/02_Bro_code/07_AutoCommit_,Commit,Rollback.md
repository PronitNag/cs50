# SQL Code Explanation - SQL Workbench

## Code Overview
Yeh SQL script transactions aur data insertion ka kaam kar rahi hai. Chaliye ek-ek karke samajhte hain:

### 1. **Transaction Control Commands**
```sql
SET AUTOCOMMIT = OFF;
COMMIT;
ROLLBACK;
```
- `SET AUTOCOMMIT = OFF;` -> Iska matlab hai ki SQL Workbench automatically har query ke baad `COMMIT` nahi karega. Matlab agar aap koi `INSERT`, `UPDATE`, ya `DELETE` karte ho to wo turant save nahi hoga.
- `COMMIT;` -> Ye manually transactions ko save karne ke liye use hota hai. Jab aap satisfied ho ki sab sahi hai, tab `COMMIT` kar ke changes permanently save kar sakte ho.
- `ROLLBACK;` -> Ye command use hoti hai changes undo karne ke liye agar `COMMIT` nahi kiya gaya ho. Matlab agar koi galat entry hui, to `ROLLBACK` se wapas purani state me aa sakte ho.

### 2. **Data Insertion**
```sql
INSERT INTO employees
VALUES	(1, 'Eugene', 'Krabs', 25.50, '2023-01-02'),
		(2, 'Squidward', 'Tentacles', 15.00, '2023-01-03'),
		(3, 'Spongebob', 'Squarepants', 12.50, '2023-01-04'),
		(4, 'Patrick', 'Star', 12.50, '2023-01-05'),
		(5, 'Sandy', 'Cheeks', 17.25, '2023-01-06');
```
- Yeh query `employees` table me naye records insert kar rahi hai.
- Columns ka order kuch is tarah hai:
  1. **ID** (Unique Employee ID)
  2. **First Name**
  3. **Last Name**
  4. **Salary** (Per hour wage)
  5. **Joining Date**
- 5 employees ka data insert ho raha hai, jo fictional characters hain.

## Summary
- Transactions ko manual control me rakhne ke liye `SET AUTOCOMMIT = OFF` use kiya gaya hai.
- `COMMIT;` aur `ROLLBACK;` ka use transactional safety ke liye hai.
- `INSERT INTO employees` command 5 employees ka data table me add kar rahi hai.

Isse ensure karna hoga ki `employees` table pehle se exist karta ho, warna error aayegi.

---
### **Agar koi aur explanation chahiye ho ya issue ho to batao!**


