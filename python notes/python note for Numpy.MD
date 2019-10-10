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
# rows and columns
# return a tuple, (row, column)
data_ndarray.shape

# internal data type
data_ndarray.dtype

# support vector operation, 
# like vector addition, subtraction, multiplication, division (unrelated to linear algebra)
sum = data_ndarray[:,1] + data_ndarray[:,2] 
ave = sum / num

# built-in methods
ndarray.min()
ndarray.max()
ndarray.mean()
ndarray.sum()

# 如果想要获得行或列的最大最小
# 使用参数 axis
ndarray.max(axis=1) # for row
ndarray.max(axis=0) # for column
```

__读取文件__
```py
data = np.genfromtxt('dist1_500_1.txt', delimiter=' ')
print(data.shape)
print(data.dtype)

# 如果文件有表头需要跳过可以使用`skip_header`跳过相关行数据
# 注意此处参数表示是行数，因此从1开始
data = np.genfromtxt('dist1_500_1.txt', delimiter=' ', skip_header='1')
```

__布尔索引(boolean indexing)__
```py
# 可以利用向量操作，获得布尔列表
print(np.array([2,4,6,8]) < 5)
# output: [True  True False False]

# 布尔列表可以作为索引
data = np.array([2,4,6,8])          
print(data[data > 4])
# output: [6 8]
```