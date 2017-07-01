# Handbook
# {Concept}
{explanation}

---
# **Python**

## data type
built-in data types are dict, list, set (which along with frozenset, replaces the deprecated sets module), and tuple
Dict has keys and values. List and tuple stores data with index, but set does not store them in order or have index.

## Class
Class is important in Object Oriented Programming(OOP). Python can make class with properties and methods. Inheritance and polymorphism can be applied.

## Lambda
lambda functions(anonymous functions), generates inline functions which does not require declarations using def ~:.
common cases which utilizes them are: 

map()
~~~~
def multiply(x):
    return (x*x)
def add(x):
    return (x+x)

funcs = [multiply, add]
for i in range(5):
    value = list(map(lambda x: x(i), funcs))
    print(value)

# Output:
# [0, 0]
# [1, 2]
# [4, 4]
# [9, 6]
# [16, 8]
~~~~

filter()
~~~~
number_list = range(-5, 5)
less_than_zero = list(filter(lambda x: x < 0, number_list))
print(less_than_zero)

# Output: [-5, -4, -3, -2, -1]
~~~~

reduce()
~~~~
from functools import reduce
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])

# Output: 24
~~~~

lambda functions help developers understand code better with less lines of code.

#  Why is Python used for Data science?

Compared to R, python is more focused on general purposes such as web app(django), prototype of native app(pyQt), hardware mockup(GPIO).
Then why is python is used for data science?

There are reasons due to its features:
- Clean syntax
- Useful Built-in Objects
- Functions and Classes which are easy to maintain
- intuitive standard library and built-in functions

However, it is packages that separates its use for scientific calculation(numpy, scipy, matplotlib).

##  Numpy
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

## Scipy
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


> *all numpy functions are applicable in columns* 

- Reindexing

~~~~
>>> color=pd.Series(['white','red','yellow','green'],
... index=[0,2,4,6])
>>> color
0     white
2       red
4    yellow
6     green
>>> color.reindex(range(7))
0     white
1       NaN
2       red
3       NaN
4    yellow
5       NaN
6     green
dtype: object
~~~~

- Summarizing and Describing 

~~~~
>>> pop
           CN      JP     KR     UK      US
2015  1376.05  126.57  50.29  64.72  321.77
2016  1382.32  126.32  50.50  65.11  324.12
>>> pop.sum()
CN    2758.37
JP     252.89
KR     100.79
UK     129.83
US     645.89
dtype: float64
>>> pop.mean()
CN    1379.185
JP     126.445
KR      50.395
UK      64.915
US     322.945
dtype: float64
>>> pop.cumsum()
           CN      JP      KR      UK      US
2015  1376.05  126.57   50.29   64.72  321.77
2016  2758.37  252.89  100.79  129.83  645.89
>>> pop.min()
CN    1376.05
JP     126.32
KR      50.29
UK      64.72
US     321.77
dtype: float64
>>> pop.max()
CN    1382.32
JP     126.57
KR      50.50
UK      65.11
US     324.12
dtype: float64
>>> pop.median()
CN    1379.185
JP     126.445
KR      50.395
UK      64.915
US     322.945
dtype: float64
>>> pop.var()
CN    19.65645
JP     0.03125
KR     0.02205
UK     0.07605
US     2.76125
dtype: float64
>>> pop.std()
CN    4.433560
JP    0.176777
KR    0.148492
UK    0.275772
US    1.661701
dtype: float64
>>> pop.describe()
               CN          JP         KR         UK          US
count     2.00000    2.000000   2.000000   2.000000    2.000000
mean   1379.18500  126.445000  50.395000  64.915000  322.945000
std       4.43356    0.176777   0.148492   0.275772    1.661701
min    1376.05000  126.320000  50.290000  64.720000  321.770000
25%    1377.61750  126.382500  50.342500  64.817500  322.357500
50%    1379.18500  126.445000  50.395000  64.915000  322.945000
75%    1380.75250  126.507500  50.447500  65.012500  323.532500
max    1382.32000  126.570000  50.500000  65.110000  324.120000
~~~~

- **Correlation Matrix Of Values** 

Correlations are important to find out the relationship between each columns in data.
(**This helps to understand relationships from raw data's columns and get a clue for the insight of the data**)

~~~~
>>> pop.corr()
     CN   JP   KR   UK   US
CN  1.0 -1.0  1.0  1.0  1.0
JP -1.0  1.0 -1.0 -1.0 -1.0
KR  1.0 -1.0  1.0  1.0  1.0
UK  1.0 -1.0  1.0  1.0  1.0
US  1.0 -1.0  1.0  1.0  1.0
~~~~

- Boolean Indexing

~~~~
>>> pop < 100
         CN     JP    KR    UK     US
2015  False  False  True  True  False
2016  False  False  True  True  False
>>> pop[pop < 100] = "yes"
>>> pop
           CN      JP   KR   UK      US
2015  1376.05  126.57  yes  yes  321.77
2016  1382.32  126.32  yes  yes  324.12
~~~~

- File IO

~~~~
pd.read_csv({file_path})
~~~~

- *Data Handling*

~~~~
>>> a
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
>>> b
   A  B  C  D
0  4  4  4  4
1  5  5  5  5
2  6  6  6  6
3  7  7  7  7
>>> result = pd.concat([a,b])
>>> result
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
0  4  4  4  4
1  5  5  5  5
2  6  6  6  6
3  7  7  7  7
~~~~

Applying keys

~~~~
>>> a
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
>>> b
   A  B  C  D
0  4  4  4  4
1  5  5  5  5
2  6  6  6  6
3  7  7  7  7
>>> c
    A   B   C   D
0   8   8   8   8
1   9   9   9   9
2  10  10  10  10
3  11  11  11  11
>>> pd.concat([a,b,c],keys=['x','y','z'])
      A   B   C   D
x 0   1   1   1   1
  1   2   2   2   2
  2   3   3   3   3
  3   4   4   4   4
y 0   4   4   4   4
  1   5   5   5   5
  2   6   6   6   6
  3   7   7   7   7
z 0   8   8   8   8
  1   9   9   9   9
  2  10  10  10  10
  3  11  11  11  11
~~~~

outer join(join with union keys)

~~~~
>>> a
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
>>> b = pd.DataFrame({'A': {2:2,3:3,6:6,7:7}, 'B': {2:2,3:3,6:6,7:7}, 'C': {2:2,3:3,6:6,7:7}, 'D': {2:2,3:3,6:6,7:7}}
>>> b
   A  B  C  D
2  2  2  2  2
3  3  3  3  3
6  6  6  6  6
7  7  7  7  7
>>> d =pd.concat([a,b],axis=1, join='outer')
>>> d
     A    B    C    D    A    B    C    D
0  1.0  1.0  1.0  1.0  NaN  NaN  NaN  NaN
1  2.0  2.0  2.0  2.0  NaN  NaN  NaN  NaN
2  3.0  3.0  3.0  3.0  2.0  2.0  2.0  2.0
3  4.0  4.0  4.0  4.0  3.0  3.0  3.0  3.0
6  NaN  NaN  NaN  NaN  6.0  6.0  6.0  6.0
7  NaN  NaN  NaN  NaN  7.0  7.0  7.0  7.0
~~~~

inner join(join with intersection keys)

~~~~
>>> a
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
>>> b
   A  B  C  D
2  2  2  2  2
3  3  3  3  3
6  6  6  6  6
7  7  7  7  7
>>> d =pd.concat([a,b],axis=1, join='inner')
>>> d
   A  B  C  D  A  B  C  D
2  3  3  3  3  2  2  2  2
3  4  4  4  4  3  3  3  3
~~~~

appending

~~~~
>>> c
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
>>> b
   A  B  C  D
2  2  2  2  2
3  3  3  3  3
6  6  6  6  6
7  7  7  7  7
>>> c.append(b)
   A  B  C  D
0  1  1  1  1
1  2  2  2  2
2  3  3  3  3
3  4  4  4  4
2  2  2  2  2
3  3  3  3  3
6  6  6  6  6
7  7  7  7  7
~~~~

Merge with multiple join keys

~~~~
>>> left
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K0   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> right
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K1   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> result = pd.merge(left,right, on=['key1','key2'])
>>> result
    A   B key1 key2   C   D
0  A0  B0   K0   K0  C0  D0
1  A2  B2   K1   K0  C1  D1
2  A2  B2   K1   K0  C2  D2
~~~~

left outer join

~~~~
>>> left
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K0   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> right
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K0   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> result = pd.merge(left,right, how='left', on=['key1', 'key2'])
>>> result
    A   B key1 key2    C    D
0  A0  B0   K0   K0   C0   D0
1  A0  B0   K0   K0   C1   D1
2  A1  B1   K0   K1  NaN  NaN
3  A2  B2   K1   K0   C2   D2
~~~~

Right outer join

~~~~
>>> left
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K0   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> right
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K0   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> result = pd.merge(left,right, how='right', on=['key1', 'key2'])
>>> result
     A    B key1 key2   C   D
0   A0   B0   K0   K0  C0  D0
1   A0   B0   K0   K0  C1  D1
2   A2   B2   K1   K0  C2  D2
3  NaN  NaN   K2   K0  C3  D3
~~~~

Inner join

~~~~
>>> left
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K0   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> right
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K0   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> result = pd.merge(left,right, how='inner', on=['key1', 'key2'])
>>> result
    A   B key1 key2   C   D
0  A0  B0   K0   K0  C0  D0
1  A0  B0   K0   K0  C1  D1
2  A2  B2   K1   K0  C2  D2
~~~~

Outer join

~~~~
>>> left
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K0   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> right
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K0   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> result = pd.merge(left,right, how='outer', on=['key1', 'key2'])
>>> result
     A    B key1 key2    C    D
0   A0   B0   K0   K0   C0   D0
1   A0   B0   K0   K0   C1   D1
2   A1   B1   K0   K1  NaN  NaN
3   A2   B2   K1   K0   C2   D2
4   A3   B3   K2   K1  NaN  NaN
5  NaN  NaN   K2   K0   C3   D3
~~~~

Joining on index

~~~~
>>> left 
     A   B
K0  A0  B0
K1  A1  B1
K2  A2  B2
>>> right
     C   D
K0  C0  D0
K2  C2  D2
K3  C3  D3
>>> result = left.join(right, how='inner')
>>> result
     A   B   C   D
K0  A0  B0  C0  D0
K2  A2  B2  C2  D2
~~~~

~~~~
>>> left 
     A   B
K0  A0  B0
K1  A1  B1
K2  A2  B2
>>> right
     C   D
K0  C0  D0
K2  C2  D2
K3  C3  D3
>>> result = left.join(right, how='outer')
>>> result
      A    B    C    D
K0   A0   B0   C0   D0
K1   A1   B1  NaN  NaN
K2   A2   B2   C2   D2
K3  NaN  NaN   C3   D3
~~~~

# Matplotlib

Matplotlib is used to plot collected datas in python. 

Basic plot

~~~~
>>> ts = pd.Series(np.random.randn(1000), index=pd.date_range('1/1/2000', periods=1000))
>>> ts = ts.cumsum()
>>> ts.plot()
<matplotlib.axes._subplots.AxesSubplot object at 0x11b43d2d0>
>>> plt.show(ts)
~~~~

![Basic plot](https://s3.ap-northeast-2.amazonaws.com/videosforlandingpage0525/basic_plot.png)

Multiple Plot

~~~~
>>> df = pd.DataFrame(np.random.randn(1000, 4), index=ts.index, columns=list('ABCD'))
>>> df = df.cumsum()
>>> df.plot()
>>> plt.show()
~~~~

![Multiple Plot](https://s3.ap-northeast-2.amazonaws.com/videosforlandingpage0525/multiple_plot.png)

Other kinds of plot can be made:

Pie chart
~~~~
>>> labels = 'Frogs', 'Hogs', 'Dogs', 'Logs'
>>> sizes = [15, 30, 45, 10]
>>> explode = (0, 0.1, 0, 0)
>>> plt.pie(sizes, explode=explode, labels=labels, autopct='%1.1f%%', shadow=True, startangle=90)
([<matplotlib.patches.Wedge object at 0x1169fdd10>, <matplotlib.patches.Wedge object at 0x11cc8c110>, <matplotlib.patches.Wedge object at 0x11cc99410>, <matplotlib.patches.Wedge object at 0x11cca6710>], [<matplotlib.text.Text object at 0x116a0d7d0>, <matplotlib.text.Text object at 0x11cc8cb50>, <matplotlib.text.Text object at 0x11cc99e50>, <matplotlib.text.Text object at 0x11ccb3190>], [<matplotlib.text.Text object at 0x116a0dc90>, <matplotlib.text.Text object at 0x11cc8cf90>, <matplotlib.text.Text object at 0x11cca62d0>, <matplotlib.text.Text object at 0x11ccb35d0>])
>>> plt.show()
~~~~

![Pie chart](https://s3.ap-northeast-2.amazonaws.com/videosforlandingpage0525/Piechart.png)

Box plot

~~~~
>>> spread = np.random.rand(50) * 100
>>> center = np.ones(25) * 50
>>> flier_high = np.random.rand(10) * 100 + 100
>>> flier_low = np.random.rand(10) * -100
>>> data = np.concatenate((spread, center, flier_high, flier_low), 0)
>>> plt.boxplot(data)
~~~~

![Box plot](https://s3.ap-northeast-2.amazonaws.com/videosforlandingpage0525/boxplot.png)


Subplot

Subplots can be added using subplot() function
f, axarr = plt.subplot({row},{column},sharex={True or False}, sharey={True or False})
ShareX or shareY : share given axis value between subplots

~~~~
"""
Tuple
"""
>>> x = np.linspace(0, 2 * np.pi, 400)
>>> y = np.sin(x * 2)
>>> f, (ax1, ax2) = plt.subplots(1, 2, sharey=True)
>>> ax1.plot(x, y)
[<matplotlib.lines.Line2D object at 0x1169db410>]
>>> ax1.set_title('Sharing Y axis')
<matplotlib.text.Text object at 0x11d311850>
>>> ax2.scatter(x, y)
<matplotlib.collections.PathCollection object at 0x1169ca650>
>>> plt.show()
~~~~

~~~~
"""
Array
"""
>>> x = np.linspace(0, 2 * np.pi, 400)
>>> y = np.sin(x * 2)
>>> f, axarr = plt.subplots(1, 2, sharey=True)
>>> axarr[0].plot(x, y)
[<matplotlib.lines.Line2D object at 0x1169db410>]
>>> axarr[0].set_title('Sharing Y axis')
<matplotlib.text.Text object at 0x11d311850>
>>> axarr[1].scatter(x, y)
<matplotlib.collections.PathCollection object at 0x1169ca650>
>>> plt.show()
~~~~


![Subplots](https://s3.ap-northeast-2.amazonaws.com/videosforlandingpage0525/subplots1.png)






# And there is a part which python shines in the field of data science....


# **Machine Learning**

## Python is the dominant programming language for creating data products/AI.

![Python rocks in AI/ML](https://www.ibm.com/developerworks/community/blogs/jfp/resource/BLOGS_UPLOADED_IMAGES/trends0.png)


Neural network


