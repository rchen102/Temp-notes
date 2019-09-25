## Dictionary

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

字典是无序的键值对
key可以是String或者Number，key必须是不可改变和可哈希的(unchangeable, hashable)
value可以是任意值包括字典，同一字典的value的类型可以混合(mix) 



- `dict = {}`: 创建空字典
- `dict[new_key] = new_value`: 添加新的key-value或修改已有的key-value
- `dict.update({})`: 同时添加多组key-value
- `dict[key]`: 访问key所对应的value，不存在则会产生KeyError
- `dict.get(key, retValue)`: 访问key，返回value，若不存在，返回retValue，默认返回None
- `dict.pop(key, retValue)`: 移除key，返回value，若不存在，返回retValue，默认返回None
- `dict.keys()`: 返回dict_keys对象，可以用`list()`转化成列表或`list(dict)`
- `dict.values()`: 返回dict_values对象，可以用`list()`转化成列表
- `dict.items()`: 返回dict_list对象(tuple)，可以用`list()`转化成列表


- `key in dict`: 返回key是否存在于dict
- `dict = {key:value for key, value in zip(names, heights)}`: 使用两个List创建字典