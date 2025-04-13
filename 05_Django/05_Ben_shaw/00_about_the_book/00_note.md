# Rulebook for Code Formatting

## Rule 1

Code words in text, **database table names**, **folder names**, **filenames** will be in **bold**.

---

## Rule 2

A block of code is set as follows:

```python
urlpatterns = [
    path('admin/', admin.site.urls), 
    path('', reviews.views.index)
]

## rule 3

 In cases where inputting and executing some code gives an immediate output, 
this is shown as follows:

```python
>>> qd.getlist("k")
 ['a', 'b', 'c']
```

In the preceding example, the code entered is qd.getlist("k") and the output is ['a', 'b', 'c'].

## rule 4

Lines of code that span multiple lines are split using a backslash ( \ ).

When the code is executed, 
Python will ignore the backslash, and 
treat the code on the next line as a direct continuation of the current line.
