# SQL Queries Explanation

## 1. **Fetch all employees**
```sql
SELECT * FROM employees;
```
### 📌 Yeh query `employees` table se saare records ko fetch karti hai.

## 2. **First & Last Name Fetch karna**
```sql
SELECT first_name, last_name FROM employees;
```
### 📌 Sirf `first_name` aur `last_name` columns ko retrieve karegi.

## 3. **Last Name aur First Name Order Change karke Fetch Karna**
```sql
SELECT last_name, first_name FROM employees;
```
### 📌 `last_name` ko pehle aur `first_name` ko baad mein fetch karegi.

## 4. **Specific Employee ID se Employee Dhoondhna**
```sql
SELECT *
FROM employees
WHERE employee_id = 1;
```
### 📌 `employee_id` = 1 wale employee ka data fetch karegi.

## 5. **Specific First Name wale Employee Ko Fetch Karna**
```sql
SELECT *
FROM employees
WHERE first_name = "Spongebob";
```
### 📌 Sirf un employees ka data aayega jinka `first_name` "Spongebob" hai.

## 6. **Minimum Salary Criteria Apply Karna**
```sql
SELECT *
FROM employees
WHERE hourly_pay >= 15;
```
### 📌 Sirf woh employees show honge jinki `hourly_pay` 15 ya usse zyada hai.

## 7. **Hire Date ke Basis pe Filter Karna**
```sql
SELECT hire_date, first_name
FROM employees
WHERE hire_date <= "2023-01-03";
```
### 📌 Employees dikhayega jo `2023-01-03` se pehle ya same date pe hire hue hain.

## 8. **Specific Employee ID ko Exclude Karna**
```sql
SELECT *
FROM employees
WHERE employee_id != 1;
```
### 📌 `employee_id` = 1 wale employee ko chhodke baaki sab ka data fetch karega.

## 9. **Hire Date NULL hone wale Employees Ko Dhoondhna**
```sql
SELECT *
FROM employees
WHERE hire_date IS NULL;
```
### 📌 Sirf un employees ka data show hoga jinki `hire_date` NULL hai.

## 10. **Hire Date NULL Nahi Hone Wale Employees Ko Dhoondhna**
```sql
SELECT *
FROM employees
WHERE hire_date IS NOT NULL;
```
### 📌 Sirf un employees ka data milega jinki `hire_date` NULL nahi hai.

