## SQL Code Explanation

### Table Creation
```sql
CREATE TABLE products (
    product_id INT,
    product_name varchar(25) UNIQUE,
    price DECIMAL(4, 2)
);
```
Yeh query ek `products` naam ki table banati hai jisme teen columns hain:
- `product_id` (Integer type)
- `product_name` (25 characters tak ka `varchar` jo UNIQUE hai, yani ek naam ek hi baar store ho sakta hai)
- `price` (Decimal format mein, jisme 4 digits total honge aur 2 decimal places honge, jaise `99.99`)

### Alter Table (Redundant UNIQUE Constraint)
```sql
ALTER TABLE products
ADD CONSTRAINT 
UNIQUE (product_name);
```
Yeh constraint `product_name` column par UNIQUE constraint lagata hai, lekin yeh pehle hi `CREATE TABLE` ke andar laga hua hai. Iska likhna redundant hai.

### Data Insertion
```sql
INSERT INTO products
VALUES (100, 'hamburger', 3.99),
       (101, 'fries', 1.89),
       (102, 'soda', 1.00),
       (103, "ice cream", 1.49);
```
Yeh query `products` table mein kuch rows insert karti hai:
- `100` -> `hamburger` -> `3.99`
- `101` -> `fries` -> `1.89`
- `102` -> `soda` -> `1.00`
- `103` -> `ice cream` -> `1.49`

**Note:** SQL mein strings single quotes `' '` mein likhe jaate hain, toh `"ice cream"` error de sakta hai. Isko `'ice cream'` likhna sahi hoga.

### Data Retrieval
```sql
SELECT * FROM products;
```
Yeh query `products` table ke saare records fetch kar legi.

## Summary
Yeh code ek `products` table create karta hai, usme data insert karta hai aur phir us data ko fetch karta hai. Lekin `ALTER TABLE` wali query redundant hai aur `ice cream` string ko single quotes mein likhna chahiye.

Agar aur koi doubt ho toh batao! 😊

