# SQL Code Explanation

## Code Overview
Yeh SQL code ek `test` naam ka table create karta hai jismein teen columns hote hain:
1. `my_date` - DATE type ka column hai jo sirf date store karega.
2. `my_time` - TIME type ka column hai jo sirf time store karega.
3. `my_datetime` - DATETIME type ka column hai jo date aur time dono store karega.

## Code Breakdown

```sql
CREATE TABLE test(
    my_date DATE,
    my_time TIME,
    my_datetime DATETIME
);
```

Yeh query ek `test` naam ka table create karti hai jismein 3 columns hain:
- `my_date`: DATE format ke liye.
- `my_time`: TIME format ke liye.
- `my_datetime`: DATETIME format ke liye.

```sql
INSERT INTO test
VALUES(CURRENT_DATE(), CURRENT_TIME(), NOW());
```

Yeh query table mein ek naya record insert karti hai:
- `CURRENT_DATE()`: System ki current date ko insert karega.
- `CURRENT_TIME()`: System ki current time ko insert karega.
- `NOW()`: System ki current date aur time dono insert karega.

```sql
SELECT * FROM test;
```

Yeh query pura table fetch karegi aur usme jo bhi data hoga, wo sab dikhayegi.

## Example Output
Agar aaj ki date `2025-04-03` aur current time `14:30:45` hai, toh table ka data kuch aisa dikh sakta hai:

| my_date  | my_time  | my_datetime         |
|----------|----------|---------------------|
| 2025-04-03 | 14:30:45 | 2025-04-03 14:30:45 |

Isse aapko system ki current date aur time ka use samajhne mein madad milegi.

## Use Cases
- Yeh table timestamps ko store karne ke liye useful ho sakta hai.
- Agar kisi system ya user ke actions ka time record karna ho toh yeh approach useful rahegi.
- SQL queries ko samajhne aur practice karne ke liye ek basic example hai.
