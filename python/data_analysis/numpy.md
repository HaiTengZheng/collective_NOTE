```python
import numpy as np
# http://www.numpy.org

np.arange(3)
# array([0, 1, 2])

np.arange(2, 6)
np.arange(start = 2, stop = 6)
# array([2, 3, 4, 5])
np.arange(start = 2, stop = 6, step = 2)
# array([2, 4])

# reshape
# reshape(2, 3)     2x3
# reshape(2, 3, 2)  2x3x3

# 随机数
np.random.randint(5)
# 0..5 之间的随机值


np.nan
# nan: not a number

# 属性
## ndim     数组的维度
np.ndim
## shape    数组每个维度的大小
np.shape
## size     数组的总大小
np.size
## dtype    数组的数据类型
np.dtype
## itemsize 每个数组元素字节大小
np.itemsize 
## nbytes   数组总字节大小
np.nbytes

# 数组切片
# x[start:stop:step]
```
