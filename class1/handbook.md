# Handbook
## 1. Why is Python used for Data science?

Compared to R, python is more focused on general purposes such as web app(django), prototype of native app(pyQt), hardware mockup(GPIO).
Then why is python is used for data science?

There are reasons due to its features:
- Clean syntax
- Useful Built-in Objects
- Functions and Classes which are easy to maintain
- intuitive standard library and built-in functions

However, it is packages that separates its use for scientific calculation(numpy, scipy, matplotlib).

## Numpy
Numpy is the python library used for calculating between separate arrays or matrices with ease.
Here are functions of Numpy:

- **Data type**

data types are used to clarify and separate with in *numpy array*(not built-in array)

(example)
"""
>>> import numpy as N
>>> dt = N.dtype([(’id’, ’i4’),
(’name’, ’S12’), (’scores’, ’u1’, 4)])
>>> a = N.array([(1001, ’James’,
[100,98,97,60]), (1002, ’Kathy’,
[100,100,85,98]), (1003, ’Michael’,
[84,75, 98,100]), (1004, ’John’,
[84,76,82,92])], dtype=dt)
>>> a[’name’]
array([’James’, ’Kathy’, ’Michael’,
’John’], dtype=’—S12’)
>>> a[’scores’]
array([[100, 98, 97, 60],
[100, 100, 85, 98],
[ 84, 75, 98, 100],
[ 84, 76, 82, 92], dtype=uint8)
"""
