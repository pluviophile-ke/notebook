## numpy的核心array 

* array本身的属性

  * shape：array各个维度的长度，返回的是一个元组

  * ndim：一个数字，表示array的维度的数目，即有几维

  * size：一个数字，表示array中所有数据元素的数目

  * dtype：array中元素的数据类型

* array本身支持的大量操作和函数

  * 直接逐元素的加减乘除等操作

  * 更好的面向多维的数组索引

  * 求sum/mean等聚合函数

  * 线性代数函数，比如求解逆矩阵、求解方程组



## 创建array的方法

* 从python的列表和嵌套列表创建array
* 使用预定函数arange、ones/ones_like、zeros/zeros_like、empty/empty_like、full/full_like、eye等函数创建
* 生成随机数的np.random模块构建


### 1.使用列表和嵌套列表创建


```python
import numpy as np
```


```python
# 创建一个一维数组
x = np.array([1,2,3,4,5,6,7,8,9])
x
```


    array([1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
# 创建一个二维数组
X = np.array(
    [
        [1,2,3],
        [6,7,8]
    ]
)
X
```


    array([[1, 2, 3],
           [6, 7, 8]])



### 2.探索数组array的属性


```python
x.shape		# 返回元组，各个维度的长度
```


    (9,)




```python
X.shape		# 返回元组，各个维度的长度
```


    (2, 3)




```python
x.ndim		# 返回维度值
```


    1




```python
X.ndim		# 返回维度值
```


    2




```python
x.size		# 返回元素个数
```


    9




```python
X.size		# 返回元素个数
```


    6




```python
x.dtype		# array中元素的数据类型
```


    dtype('int32')




```python
X.dtype		# array中元素的数据类型
```


    dtype('int32')



### 3.创建array的便捷函数

1. 使用arange创建数字序列

   * arange([start,] stop[,step], dtype=None)

   ```python
   print(np.arange(10))			# [0 1 2 3 4 5 6 7 8 9]
   print(np.arange(0, 10))			# [0 1 2 3 4 5 6 7 8 9]
   print(np.arange(1, 10))			# [1 2 3 4 5 6 7 8 9]
   print(np.arange(0, 10, 2))		# [0 2 4 6 8]
   ```



2. 使用ones创建全是1的数组

   * np.ones(shape, dtype=None, order='C')
   * shape: int or tuple of ints Shape of the new array, e.g.(2, 3) or 2.

   ```python
   print(np.ones((2,3)))
   print(np.ones(10))
   ```

   ```
   [[1. 1. 1.]
    [1. 1. 1.]]
   [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
   ```

   

3. 使用ones_like创建形状相同的数组

   * ones_like(a, dtype=float, order='C')

   ```python
   print(X.shape)
   print(np.ones_like(X))
   ```

   ```
   (2, 3)
   [[1 1 1]
    [1 1 1]]
   ```

   

4. 使用zeros创建全是0的数组

   * np.zeros(shape, dtype=None, order='C')

   ```python
   print(np.zeros((2, 4)))
   ```

   ```
   [[0. 0. 0. 0.]
    [0. 0. 0. 0.]]
   ```

   

5. 使用zeros_like创建形状相同的数组

   * np.zeros_like(a, dtype=float, order='C')

   ```python
   print(X.shape)
   print(np.zeros_like(X))
   ```

   ```
   (2, 3)
   [[0 0 0]
    [0 0 0]]
   ```



6. 使用empty创建全是0的数组

   * empty(shape, dtype=float, order='C')

   **注意：数据是未初始化的，里面的值可能是随机值**

   ```python
   print(np.empty(10))
   print(np.empty((3,4)))
   ```

   ```\
   [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
   [[1.62008637e-311 3.16202013e-322 0.00000000e+000 0.00000000e+000]
    [1.16709769e-312 5.64358755e-062 9.59904746e-071 6.52054982e-038]
    [4.88946699e-033 6.95911306e-042 1.24481012e-047 1.24508050e-047]]
   ```

   

7. 使用empty_like创建形状相同的数组

   * empty_like(prototype, dtype=None

   ```python
   np.empty_like(X)
   ```

   ```
   array([[0, 0, 0],
          [0, 0, 0]])
   ```

   

8. 使用full创建指定值的数组

   * np.full(shape, fill_value, dtype=None, order='C')

   ```python
   np.full(10, 666)
   ```

   ```
   array([666, 666, 666, 666, 666, 666, 666, 666, 666, 666])
   ```

   

   ```python
   np.full((2,4), 333)
   ```

   ```
   array([[333, 333, 333, 333],
          [333, 333, 333, 333]])
   ```



9. 使用full_like创建形状相同的数组

   * np.full_like(a, fill_value, dtype=None)

   ```python
   np.full_like(X, 888)
   ```

   ```
   array([[888, 888, 888],
          [888, 888, 888]])
   ```



10. 使用random模块生成随机数的数组

    * randn(d0, d1, ..., dn)

    ```python
    np.random.randn()
    ```

    ```
    0.44271203177956087
    ```

    

    ```python
    np.random.randn(3)
    ```

    ```
    array([-0.53090449,  1.39778766,  0.97949094])
    ```

    

    ```python
    np.random.randn(3,2)
    ```

    ```
    array([[-1.12911303, -1.03716249],
           [-0.22956464,  0.71884899],
           [-0.249187  , -0.33226493]])
    ```

    ```python
    np.random.randn(3, 2, 4)
    ```

    ```
    array([[[-0.00654989,  0.14614851, -0.76659919,  0.21227405],
            [ 0.56737005,  0.6072022 , -0.81390333,  1.3888022 ]],
    
           [[ 1.3649362 , -0.91648233, -0.61200986, -0.92991811],
            [ 0.51101019,  0.66149372, -1.62169522,  1.79904655]],
    
           [[-0.13513549, -1.78206212, -0.51992804,  1.66364678],
            [ 0.31529671,  0.38824006, -0.30265983, -2.01916843]]])
    ```



### 4.array本身支持的大量操作和函数


```python
A = np.arange(10).reshape(2, 5)
A
```


    array([[0, 1, 2, 3, 4],
           [5, 6, 7, 8, 9]])




```python
A.shape
```


    (2, 5)




```python
A+1
```


    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10]])




```python
A*3
```


    array([[ 0,  3,  6,  9, 12],
           [15, 18, 21, 24, 27]])




```python
np.sin(A)
```


    array([[ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ],
           [-0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849]])




```python
np.exp(A)
```


    array([[1.00000000e+00, 2.71828183e+00, 7.38905610e+00, 2.00855369e+01,
            5.45981500e+01],
           [1.48413159e+02, 4.03428793e+02, 1.09663316e+03, 2.98095799e+03,
            8.10308393e+03]])




```python
B = np.random.randn(2, 5)
B
```


    array([[-0.13981227,  2.56666337, -1.51516605,  0.61149834,  0.32321457],
           [-1.47994646,  0.23412785,  0.07835843,  0.15183485, -0.33465361]])




```python
A+B
```


    array([[-0.13981227,  3.56666337,  0.48483395,  3.61149834,  4.32321457],
           [ 3.52005354,  6.23412785,  7.07835843,  8.15183485,  8.66534639]])




```python
A-B
```


    array([[ 0.13981227, -1.56666337,  3.51516605,  2.38850166,  3.67678543],
           [ 6.47994646,  5.76587215,  6.92164157,  7.84816515,  9.33465361]])


