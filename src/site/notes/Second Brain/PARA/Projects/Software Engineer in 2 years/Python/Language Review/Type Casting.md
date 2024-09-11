---
{"dg-publish":true,"dg-path":"Projects/Software Engineer in 2 years/Python/Language Review/Type Casting.md","permalink":"/projects/software-engineer-in-2-years/python/language-review/type-casting/","noteIcon":"","updated":"2024-09-11T10:02:56.617-07:00"}
---

>[!link] Type Casting is the process of converting data of one type to another

Python has two types of conversion:

1. Implicit - automatic type conversion 
2. Explicit - manual type conversion

## Example
```python
int_num = 123
float_num = 1.23

new_num = int_num + float_num

print("Value:", new_num)
# 124.23
print("Data Type:", type(new_num))
# Data Type: <class 'float'>
```

> smaller data types implicitly get converted to larger data types to avoid loss of data

Python can't perform implicit conversions on mis-matched data types

can't add `str` and `int` for example: `'12' + 23`

## Explicit Conversions
---

users convert the data type of an object to required data type

you can use [[What are Built-in Functions \| built-in functions]] like `int()`, `float()`, `str()` to perform explicit type conversions

```python
num_string = '12'
num_integer = 23

# Type conversion
print(num_integer + int(num_string))
# output: 35
```







