## 函数

参考
[Python3教程|菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

### 声明定义
使用关键字`def`定义函数
利用缩进(indentation)来控制函数范围

```python
def function_name(formal parameter):
    some code
```

### 作用域
函数内变量作用域仅在函数内，函数外的变量作用域则可能包含函数内

```python
def create_special_string(special_item):
    year = 2019
    return str(year) + ", Our special is " + special_item + "."

print(special_item) 
print(year)  # Both will get: NameError: 'special_item' is not defined

header_string = "Our special is " 
def create_special_string(special_item):
    return header_string + special_item + "."

print(create_special_string("grapes")) # print Our special is grapes.

```


### 参数
- 位置参数(positional argument)
调用函数时必须a按正确的位置顺序传入参数

```python
def divide(n1, n2):
    print(n1 / n2)
divide(4, 2) #print 2
```

- 关键字参数(keyword argument)
允许调用函数时，参数顺序与声明顺序不同
关键字参数必须跟随在位置参数之后
```python
def divide(n1, n2):
    print(n1 / n2)
divide(n2 = 2, n1 = 6) #print 3
divide(6, n2 = 2) # print 3
divide(n1 = 6, 2) # Error: positional argument follows keyword argument
```

- 默认参数(default argument)
调用函数时，如果默认参数的值没有传入，则被认为是默认值
拥有默认值的参数之后不能放置普通参数

```python
def divide(n1, n2 = 2):
    print(n1 / n2)
divide(8) #print 4

# Wrong
def divide(n1 = 6, n2):
    print(n1 / n2)

# multi default arguments
def test_fun(first, second = "second", third = "third"):
    print(first + " | " + second + " | " + third)

test_fun("test", "where I will be") # print test | where I will be | third
```

### return
不同于java，python可以返回多个值
```python
def square_point(x_value, y_value):
    x_2 = x_value * x_value
    y_2 = y_value * y_value
    return x_2, y_2
x_squared, y_squared = square_point(1, 3)
```
