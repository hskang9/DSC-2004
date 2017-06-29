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
Although it has a lot of features, we focus on data science so I will only talk about pandas.

### **Pandas**

Pandas is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.

it uses a special object which is called 'DataFrame' to process data. 
DataFrames are similar to python dictionary, but they are different in structures and features.
They use 'name' as key, and stores value which corresponds to it regardless of data type(even dictionary), and a set of name and data is called as a 'column'.
Also, they have functions which manipulates the content.

DataFrames are also integrates with numpy, so numpy functions or calculation can be applied to them.

- Initialization

~~~~
>>> df = pd.DataFrame(np.random.randn(10,5), columns=['a','b','c','d','e'])
>>> df
          a         b         c         d         e
0 -1.331539  1.958928  0.795523 -0.012123 -0.663218
1  0.930204 -2.687991  0.166150  0.285672  0.391856
2 -1.449307  1.083694 -0.547790 -0.414167 -2.354428
3 -0.142876 -0.454380 -1.214627  2.218012 -1.009829
4  0.567735 -1.305605 -0.793925  0.312255  2.142604
5 -0.374101 -0.644294  0.433977  0.362608 -0.243922
6 -0.794533  0.735908 -1.296882  0.152835  2.356051
7  0.754404 -1.214098  0.231807 -0.069859 -0.402979
8 -0.483729 -2.367157  0.112239  1.431582 -1.622971
9  0.822402  0.646229  1.384360  0.322538 -2.048547

"""
Initializing dictionary as value
"""

>>> pop_data = {'KR': {2015:50.29, 2016:50.50},
 'US': {2015:321.77, 2016:324.12},
 'CN': {2015:1376.05, 2016:1382.32},
 'JP': {2015:126.57, 2016:126.32},
 'UK': {2015:64.72, 2016:65.11}}
>>> pop = pd.DataFrame(pop_data)

>>> pop
           CN      JP     KR     UK      US
2015  1376.05  126.57  50.29  64.72  321.77
2016  1382.32  126.32  50.50  65.11  324.12

~~~~

- Adding column

df[{new column name}] = {new values}

~~~~
>>> df['f'] = pd.Series(np.random.randn(10))
>>> df
          a         b         c         d         e         f
0 -1.331539  1.958928  0.795523 -0.012123 -0.663218  0.352690
1  0.930204 -2.687991  0.166150  0.285672  0.391856 -0.582114
2 -1.449307  1.083694 -0.547790 -0.414167 -2.354428 -0.045298
3 -0.142876 -0.454380 -1.214627  2.218012 -1.009829  0.144737
4  0.567735 -1.305605 -0.793925  0.312255  2.142604  0.177322
5 -0.374101 -0.644294  0.433977  0.362608 -0.243922 -0.051650
6 -0.794533  0.735908 -1.296882  0.152835  2.356051 -0.034101
7  0.754404 -1.214098  0.231807 -0.069859 -0.402979 -0.146271
8 -0.483729 -2.367157  0.112239  1.431582 -1.622971  0.517037
9  0.822402  0.646229  1.384360  0.322538 -2.048547  0.563735
~~~~

- Cropping column

~~~~
>>> df['a']
0   -1.331539
1    0.930204
2   -1.449307
3   -0.142876
4    0.567735
5   -0.374101
6   -0.794533
7    0.754404
8   -0.483729
9    0.822402
Name: a, dtype: float64
~~~~

- Calculation(Same as numpy)

~~~~
>>> df['a']/ df['b']
0   -0.679728
1   -0.346059
2   -1.337377
3    0.314442
4   -0.434844
5    0.580638
6   -1.079663
7   -0.621370
8    0.204350
9    1.272616
dtype: float64
~~~~

"""
### *all numpy functions are applicable in columns* 
"""


- File IO

~~~~
pd.read_csv({file_path})
~~~~





