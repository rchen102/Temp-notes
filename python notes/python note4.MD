## 列表List
Tuple

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

List可以同时存储Numbers和String
List可以存储List
使用`+`连接List

```python
empty_list = []
ints_and_strings = [1, 2, 3, 'four', 'five']
```

### List相关函数
- `list[idx]`: 访问元素
  可以使用负数表示“倒数”，`-1`表示最后一个元素
- `list[start:end]`: 返回List切片(slicing)
  可以省略`start`则表示从第一个元素开始，省略`end`表示到最后一个元素
- `list.append(element)`: 添加元素
- `element = list.pop()`: 移除并返回最后一个元素
- `list.count(element)`: 统计元素出现次数
- `list.sort()`: 按numerical或者alphabetical排序，改变原List，没有返回
  逆序: `list.sort(reverse=True)`
  另一种排序方法是使用`sorted(list)`: 不改变原本List，返回排序后的新List
  ```python
  names_and_age = [["Sam" , 23], ["Vik", 30], ["Phil", 26], ["John", 18]]
  names_and_age.sort(key = lambda x: x[1])
  print(names_and_age)

  # Output:
  [['John', 18], ['Sam', 23], ['Phil', 26], ['Vik', 30]]
  ```
- `len(list)`: 返回List长度

- `list(zip(list1, list2))`: 返回元组列表
- `list(range(n))`: 返回[0,...,n-1]列表(consecutive numbers)
  `list(range(n1, n2))`: 返回[n1,...,n2-1]列表
  `list(range(n1, n2, step))`: 返回[n1,...,n2-1]列表
