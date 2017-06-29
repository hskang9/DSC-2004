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

## 2. Numpy
Numpy is the python library used for calculating between separate arrays or matrices with ease with multiple data types.
Since most python library for manipulating data uses this library,it is imported in almost every data science projects in python.

Here are features of Numpy:

- **Data type**

data types are used to clarify and separate in *numpy array*(not built-in array)

(example) ** Declaring data type of numpy array, the array can be used similarly as dictionary. **

~~~~
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
~~~~

- **Methods and Attributes**

Here are useful functions and attributes in numpy that is used always.

- Attributes(shape of numpy array, data type)

~~~~
>>> a.shape
(3,)
>>> a.dtype
dtype('int64')
~~~~

- Methods

**Calculation**
~~~~
>>> a = np.array([1,2,3])
>>> b = np.array([4,5,6])
>>> a+b
array([5, 7, 9])
>>> a-b
array([-3, -3, -3])
>>> a*b
array([ 4, 10, 18])
>>> b/a
array([4, 2, 2]) 
>>> b/a.astype(float) # astype() function determines returning type of result
array([ 4. ,  2.5,  2. ])
~~~~

**Type Representation**

As explained above,
~~~~
>>> a.astype(unicode)
array([u'1', u'2', u'3'], 
      dtype='<U21')
>>> a.astype('double')
array([ 1.,  2.,  3.])
~~~~

**Linear Algebra**
~~~~
>>> a = np.ones((2,3), np.dtype(int))
>>> a
array([[1, 1, 1],
       [1, 1, 1]])
>>> a.T # Transpose
array([[1, 1],
       [1, 1],
       [1, 1]])
 >>> a.reshape(1,6) # reshape
array([[1, 1, 1, 1, 1, 1]])
>>> a.reshape(6,1)
array([[1],
       [1],
       [1],
       [1],
       [1],
       [1]])
~~~~

**Data Manipulation**

Filtering

~~~~
>>> x = np.arange(9.).reshape(3, 3)
>>> np.where( x > 5 )
(array([2, 2, 2]), array([0, 1, 2]))
>>> x[np.where( x > 3.0 )]               
array([ 4.,  5.,  6.,  7.,  8.])
~~~~

Sorting

~~~~
>>> a = np.array([[1,4],[3,1]])
>>> np.sort(a)                # sort along the last axis
array([[1, 4],
       [1, 3]])
>>> np.sort(a, axis=None)     # sort the flattened array
array([1, 1, 3, 4])
>>> np.sort(a, axis=0)        # sort along the first axis
array([[1, 1],
       [3, 4]])
~~~~

## 3. Scipy
Scipy is scientific computing library in python. 
