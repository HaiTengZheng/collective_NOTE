# pandas
> import pandas as pd

# .read_csv 
read csv file
> pd.read_csv("example.csv")

# Object: Series
- 与 python 字典的区别：Series 中的索引可以重复
## `pd.Series` class is a template
create a `Series` object from the Series class
> pd.Series()

## parameters
six
- data
- index
- dtype
- name
- copy
- fastpath

## 缺失值
使用 Numpy 的 nan 对象
nan: not a number
表示空值或不存在
