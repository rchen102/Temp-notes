## 基础


### Introduction
Python is a high-level language, which takes less time to program, but also less control over prformance

### print
使用""或者''都可以，但是最好保持一致(consistent)
当String中包含""或''时，可以灵活使用，避免提前截断

```python
print("Hello World!")
print('Hello World')
```

## 变量/Variable
Python变量不需要声明类型，可以直接使用
每个变量相当于一个box，可以放置任意类型变量
命名习惯使用__Snake Case__

## Error
SyntaxError
NameError
TypeError
IndexError
ZeroDivisionError

## 标准变量类型

Numbers
String
Bool
List
Tuple
Dictionary

type(variable) # return type of variable

Numbers
- int
- float
- String to int: `int(str)`

String
- 可以利用`+`连接字符串(concatenate string)
- 可以利用`*`复制字符串(repeat string)
- 在连接其他非字符串时，先使用`str()`将其他类型转化为字符串
- 多行String使用三个引号`"""` 或者 `'''`

```py
str1 = "My age is "
age = 12
str2 = str1 + str(age) + str1
# Another way to concatenate string
# Just pass variables as arguments
print(str1, age, str2)
str = """
Come on!
You are the best!
"""
```

Bool
- `True` or `False`

可更改(mutable)与不可更改(immutable)对象
在 python 中，strings, tuples, 和 numbers 是不可更改的对象，而 list,dict 等则是可以修改的对象

- 不可变类型：变量赋值 a=5 后再赋值 a=10，这里实际是新生成一个 int 值对象 10，再让 a 指向它，而 5 被丢弃，不是改变a的值，相当于新生成了a

- 可变类型：变量赋值 la=[1,2,3,4] 后再赋值 la[2]=5 则是将 list la 的第三个元素值更改，本身la没有动，只是其内部的一部分值被修改了

python 函数的参数传递：

- 不可变类型：类似 c++ 的值传递，如 整数、字符串、元组。如fun（a），传递的只是a的值，没有影响a对象本身。比如在 fun（a）内部修改 a 的值，只是修改另一个复制的对象，不会影响 a 本身。

- 可变类型：类似 c++ 的引用传递，如 列表，字典。如 fun（la），则是将 la 真正的传过去，修改后fun外部的la也会受影响

## None

None is a special value in Python. It is unique (there can’t be two different Nones) and immutable (you can’t update None or assign new attributes to it).

`None` is falsy: in if statement it will be considered as false
`None` is unique: test something is `Node` use `is`

```py
if something is None:
    // do something
if something is not None:
    // do something
```



## 运算符
赋值运算符
`+=, -=, etc`

算术运算符
`+,-,*,/,%,**`

    除法
    python在做除法时，会先将`int`转换成`float` 
    python2.7以前的版本，如果操作数都是int，则会向下取整(round down)
    当除数是0时会出现：`ZeroDivisionError`

    乘方
    python使用`**`计算乘方
    ```python
    print(2 ** 10)  # print 1024
    ```

布尔逻辑运算符(Boolean Operator)
- `and`, `or`, `not`

