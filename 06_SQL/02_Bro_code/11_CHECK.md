## SQL Code Explanation - employees Table

### 1. **Table Creation (`CREATE TABLE`)**
Yeh query `employees` naam ka table create karti hai jisme yeh columns hain:
- `employee_id`: Integer type
- `first_name`: 50 characters tak ka string
- `last_name`: 50 characters tak ka string
- `hourly_pay`: Decimal type (5 digits, 2 decimal places)
- `hire_date`: Date type

**Constraint:** `chk_hourly_pay` yeh ensure karta hai ki `hourly_pay` ki minimum value 10.00 honi chahiye.

```sql
CREATE TABLE employees(
    employee_id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    hourly_pay DECIMAL (5, 2),
    hire_date DATE, 
    CONSTRAINT chk_hourly_pay CHECK (hourly_pay >= 10.00)
);
```

### 2. **Adding Constraint Again (`ALTER TABLE` ke through)**
Yeh code fir se same constraint `chk_hourly_pay` ko `employees` table me add kar raha hai. Lekin yeh redundant hai kyunki constraint pehle se hi create ho chuka hai.

```sql
ALTER TABLE employees
ADD CONSTRAINT chk_hourly_pay CHECK (hourly_pay >= 10.00);
```

### 3. **Inserting Data (`INSERT INTO`)**
Is query me ek naye employee ka record insert ho raha hai:
- `employee_id = 6`
- `first_name = "Sheldon"`
- `last_name = "Plankton"`
- `hourly_pay = 5.00` ❌ (Lekin yeh constraint violate karega)
- `hire_date = "2023-01-07"`

Kyuki `hourly_pay` ka constraint minimum 10.00 hai, yeh query error de degi.

```sql
INSERT INTO employees
VALUES (6, "Sheldon", "Plankton", 5.00, "2023-01-07");
```

### 4. **Removing Constraint (`ALTER TABLE DROP CHECK`)**
Yeh query `chk_hourly_pay` constraint ko hata rahi hai taaki koi bhi value `hourly_pay` me insert ho sake.

```sql
ALTER TABLE employees
DROP CHECK chk_hourly_pay;
```

### **Final Conclusion**
- Pehle ek table create hota hai aur ek constraint lagta hai jo `hourly_pay` ko 10.00 se kam hone se rokta hai.
- Fir ussi constraint ko dubara add karne ki koshish hoti hai jo unnecessary hai.
- Phir ek invalid data insert karne ka try kiya jata hai jo constraint violation karega.
- Last me constraint hata diya jata hai taaki invalid data insert ho sake.

✅ **Suggestion:**
- `ALTER TABLE ADD CONSTRAINT` ko dobara likhne ki zaroorat nahi hai.
- Agar pehle hi `hourly_pay` constraint hatane ka plan hai toh pehle constraint na lagana better hoga.
