# 🐍 Python Variables – Basic Notes (Hinglish)

### variable = a container for a value.
### A varaible Behaves as if the value that it contains

Python mein variables ka use data ko store karne ke liye hota hai. Jab hum variable banate hain, toh Python automatically uska type samajh jaata hai.

---

## 📌 1. String (str)

String matlab text ya characters ka group.

```python
name = "Amit"
city = 'Delhi'

print(name)
print(type(name))  # <class 'str'>
```

📝 Tip: Strings ko single ya double quotes mein likhte hain.

---

## 📌 2. Integer (int)

Integers matlab poore numbers bina decimal ke.

```python
age = 25
year = 2025

print(age)
print(type(age))  # <class 'int'>
```

---

## 📌 3. Float

Float matlab numbers jinmein decimal point ho., floating point number

```python
price = 99.99
pi = 3.14

print(price)
print(type(price))  # <class 'float'>
```

---

## 📌 4. Boolean (bool)

Boolean sirf do values leta hai: `True` ya `False`.

```python
is_student = True
has_passport = False

print(is_student)
print(type(is_student))  # <class 'bool'>
```

```python
is_student = False
if is_student:
  print("You are a student")
else:
  print("You are not a student")
```

---

## ℹ️ Extra Info

- Variable names letters ya underscore se start karte hain. Example: `name`, `_value`.
- Variable names mein spaces allowed nahi hote. Use underscores instead: `my_name`.

---

## ✅ Summary Table

| Type     | Example        | Description              |
|----------|----------------|--------------------------|
| String   | `"hello"`      | Text ya characters       |
| Integer  | `100`          | Whole number             |
| Float    | `99.99`        | Number with decimal      |
| Boolean  | `True` / `False` | True ya False value   |

---

---

## 📌 5. f-Strings (Formatted Strings)

f-Strings ka use tab hota hai jab humein variables ko string ke andar use karna ho.

```python
name = "Amit"
age = 25

print(f"My name is {name} and I am {age} years old.")
```

📝 Tip: f-Strings ko Python 3.6+ mein introduce kiya gaya tha. Yeh readable aur easy hota hai jab aapko string mein variable insert karna ho.

---
