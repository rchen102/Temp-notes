## String

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

- `str[idx]`: 同List一样，使用index访问字母
- `str[start:end]`: 返回str切片(slicing)
- 可以使用`for`或者`while`遍历字符串
- 不可变性Immutable
- 转义字符Escape characters
- `letter in word`: 返回True，如果字符串word包含letter，否则返回False

String方法
- `str.lower(), str.upper(), str.title()`: 返回新字符串，大小写切换和每个单词首字母大写
- `str.split(delimiter)`: 返回分割后的字符串List，默认以空格作为分割，__注意__：若是界定符等于最后一个字符，则返回后的List最后一位为空字符串
- `delimiter.join(list_you_want_to_join)`: 与split相反，返回连接后的新字符串，如果使用`,`，则可以得到CSV(comma separated variables)
- `str.strip(character)`: 去除首尾字符，默认去除空格，返回新字符串
- `str.replace(replaced, new)`: 置换字符串，返回新字符串
- `str.find(target, beg=0, end=len(string))`: 返回目标字符串在str首次出现索引，否则-1
- `“Hello, my name is {}”.format('renze')`: 格式化字符串
  `“{0} and {1}”.format('renze', 'chen')`: 可以设置指定位置
  `“{first} and {last}”.format(first='renze', last='chen')`: 可以使用参数
  `{}`实际可以设置格式参数，如保留小数点位数等
  
    
