## Numpy

参考
[Dataquest | Introduction to Numpy](https://app.dataquest.io/m/289/introduction-to-numpy)

### 介绍
Take advantage of Single Instruction Multiple Data(SIMD)
Vectorization

__创建__
```py
import numpy as np

# convert list to ndarray
data_ndarray = np.array([1, 2, 3, 4])
```

__访问__
```py
# rows and columns
# return a tuple, (row, column)
data_ndarray.shape

# access data
data_ndarray[row_idx, column_idx]
data_ndarray[row_idx]
data_ndarray[:, column_idx]

# access using list
# select 1, 3, 5 columns 
columns = [1,3,5]
data_ndarray[:, columns] 
```

__操作__
```py
# support vector operation, 
# like vector addition, subtraction, multiplication, division (unrelated to linear algebra)
sum = data_ndarray[:,1] + data_ndarray[:,2] 
ave = sum / num

# built-in methods
ndarray.min()
ndarray.max()
ndarray.mean()
ndarray.sum()
```