# Python के मूल तत्व (Python Basics)

## 1. Print और Comments

### Print Statement
Python में `print()` function का इस्तेमाल data को screen पर display करने के लिए किया जाता है।

```python
print("Hello, World!")  # यह "Hello, World!" screen पर display करेगा
print(42)               # Numbers को भी print कर सकते हैं
print("Age:", 25)       # Multiple values को एक साथ print कर सकते हैं
```

### Comments
Comments code को समझाने के लिए use किए जाते हैं और Python interpreter इन्हें ignore करता है।

```python
# यह single-line comment है

"""
यह multi-line comment है
जिसमें आप कई lines लिख सकते हैं
"""

'''
यह भी multi-line comment है
triple quotes से बना हुआ
'''

x = 5  # इस line के end में comment
```

## 2. Indentation

Python में indentation का बहुत महत्व है। अन्य programming languages में जहां brackets `{}` का use होता है, वहीं Python में code blocks को define करने के लिए indentation (spaces) का use होता है।

```python
# Correct indentation
if True:
    print("This is correctly indented")
    if True:
        print("This is nested and correctly indented")

# Incorrect indentation
if True:
print("This will cause an IndentationError")
```

Python में आमतौर पर 4 spaces की indentation use की जाती है।

## 3. Variable और Variable Assignment

Variable एक container है जिसमें data store किया जाता है।

```python
name = "Rahul"        # String variable
age = 25              # Integer variable
height = 5.9          # Float variable
is_student = True     # Boolean variable

# Multiple assignment
x, y, z = 10, 20, 30

# Value swapping
a = 5
b = 10
a, b = b, a  # अब a=10 और b=5 हो जाएगा
```

Python में variable names:
- Letters, numbers और underscore `_` से बन सकते हैं
- Number से start नहीं हो सकते
- Case-sensitive होते हैं (x और X अलग variables हैं)
- Reserved keywords नहीं हो सकते (जैसे if, for, while)

## 4. Numeric Data

Python में three main numeric data types हैं:

```python
integer_num = 42        # Integer (int) - पूर्णांक
float_num = 3.14159     # Float - दशमलव संख्या
complex_num = 3 + 4j    # Complex - मिश्रित संख्या
```

Numbers के साथ built-in functions:
```python
abs(-5)                 # 5 (absolute value)
round(3.75)             # 4 (roundoff)
round(3.75, 1)          # 3.8 (roundoff to 1 decimal place)
```

## 5. Arithmetic Operations

Python में basic arithmetic operations:

```python
addition = 5 + 3        # 8
subtraction = 10 - 4    # 6
multiplication = 6 * 7  # 42
division = 20 / 5       # 4.0 (always returns float)
floor_division = 20 // 6   # 3 (discards decimal part)
modulus = 17 % 5        # 2 (remainder)
exponent = 2 ** 3       # 8 (2 raised to power 3)
```

## 6. PEDMAS (Order of Operations)

PEDMAS/BODMAS rule arithmetic operations के order को define करता है:

- **P**: Parentheses (brackets) - सबसे पहले
- **E**: Exponents (powers) - दूसरा
- **D**: Division - तीसरा
- **M**: Multiplication - चौथा
- **A**: Addition - पांचवां
- **S**: Subtraction - आखिरी

```python
result = 10 + 3 * 2     # 16 (not 26), multiplication पहले होगा
result = (10 + 3) * 2   # 26, parentheses में operations पहले होंगे
```

## 7. Augmented Assignments

Augmented assignments shorthand हैं जो variable पर operation और assignment को combine करते हैं:

```python
x = 10
x += 5    # x = x + 5 के बराबर, अब x = 15
x -= 3    # x = x - 3 के बराबर, अब x = 12
x *= 2    # x = x * 2 के बराबर, अब x = 24
x /= 4    # x = x / 4 के बराबर, अब x = 6.0
x //= 2   # x = x // 2 के बराबर, अब x = 3.0
x %= 2    # x = x % 2 के बराबर, अब x = 1.0
x **= 3   # x = x ** 3 के बराबर, अब x = 1.0
```

इन augmented operators से code लिखना fast और readable हो जाता है।

---

इस गाइड को GitHub पर save करने के लिए `.md` extension के साथ file create करें और यह content copy-paste करें। इससे आपको Python के basic concepts का अच्छा overview मिल जाएगा।
