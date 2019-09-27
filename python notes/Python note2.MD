## 函数

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)
[Python3教程|菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
[Python函数参数默认指的陷阱和原理探究](http://cenalulu.github.io/python/default-mutable-arguments/)

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
    parameter和arument区别：
    A parameter is a variable in the definition of a function.
    An argument is the value being passed into a function call.

__位置参数__(positional argument)
调用函数时必须按正确的位置顺序传入参数

__默认参数__(default argument)
调用函数时，如果默认参数的值没有传入，则被认为是默认值
定义函数时，默认参数不能放在普通参数前面
```python
def sayhi(name, greeting="Hello"):
    print(greeting + ", " + name)
sayhi("rchen102") # prints "Hello, rchen102 "

# Raise TypeError
def sayhi(greeting="Hello", name):
    print(greeting + ", " + name)

# multi default arguments
def test_fun(first, second = "second", third = "third"):
    print(first + " | " + second + " | " + third)
test_fun("test", "where I will be") # print "test | where I will be | third"
```

__关键字参数__(keyword argument)
允许调用函数时，参数顺序与声明时的顺序不同
常常配合具有多个可选的默认参数使用
```py
def greet(message="Hello",  say=True, name="guest"):
    if say:
        print(message + ", " + name)
greet(message="Hi", name="rchen102") # print "Hi, rchen102"
```

__可变参数__
`unpacked positional parameter`: 可以使用`*agrs`接受任意数量的参数(agrs名字可以更改)
`unpacked keyword parameter`: 可以使用`**kwagrs`接受任意数量的关键字参数
对于可变参数，可以使用容器传递参数，传入时需要用`*`和`**`解构(deconstruct)
```py
def say(greeting, *agrs):
    print(greeting)
    for arg in agrs:
        print(arg)
say("Hi", "Hello", "rchen102")
strs = ["Hi", "Hello", "rchen102"]
say(*strs)
# print
# "Hi"
# “Hello"
# "rchen102"

def greet(**kwargs):
    print(kwargs) # kwargs
    print(kwargs.get('name'))
greet(name="rchen102", age=22)
dicts = {"name": "rchen102", "age": 22}
greet(**dicts)
# print
# {'name': 'rchen102', 'age': 22}
# rchen102
```

__混合使用各种参数__
按以下顺序使用：
- 位置参数
- 数量可变的位置参数`*args`
- 关键字参数
- 数量可变的关键字参数`**kwargs`

### 返回
python所有函数都有返回值，如果函数没有显式使用`return`，函数实际仍然会返回`None`
```py
def say_hello():
    print("Hello")

reveive = say_hello()
print(reveive) # print None

def reply(money):
    if money > 10:
        return "Hi"
    return # it will return None
```

python可以有多个返回值
```python
def move_point_rightup(x, y):
    x = x + 1
    y = y + 1
    return x, y

res = move_point_rightup(1, 2) # return a tuple
x = res[0]
y = res[1]

# or unpacking return
x, y = move_point_rightup(1, 2)
```

### 特别注意
__不要使用可变对象作为函数的默认参数__
```py
def add_item(nums=[], n=1):
    nums.append(n)
    return nums

print(add_item()) # print [1] expected result
print(add_item()) # print [1, 1] something unexpected
print(add_item()) # print [1, 1, 1]
```
出现问题的原因：
函数也是对象，当python解释器遇到def，会在内存中创建一个函数对象
在全局命名空间会有一个变量(add_item)指向该对象，不管函数调用多少次，函数对象仅有一个
函数对象具有属性名字(`__name__`)和默认参数列表(`__defaults__`)，

调用函数时，如果没有显示传入参数，该参数会获得函数def阶段就创建的默认参数对象的一个指针
如果默认参数是可变的，在函数体内对参数的修改，实际上都是对默认参数对象指向的内存的修改
如果默认参数是不可变的，如果在函数体内对该参数进行修改，参数会指向另一个新的不可变值

改进
```py
def add_item(nums=None, n=1):
    if nums is None:
        nums = []
    nums.append(n)
    return nums
```

__Decorator__
函数也是对象，可以在函数中定义函数
```py
def test(n1, n2):
    def add(n1, n2):
        return n1 + n2
    return add(n1, n2)
print(test(1, 2)) # prints 3
```

函数可以作为返回值
```py
def math_func(name):
    def add(n1, n2):
        return n1 + n2
    if name == 'add':
        return add

add_func = math_func('add')
print(add_func)       # <function math_func.<locals>.add at 0x000002490C24AB70>
print(add_func(1, 2)) # 3

```

Decorate a cuntion
```py
def hello_decorator(print_func):
    def wrapper():
        print("Hello!")
        print_func()
    return wrapper

def print_name():
    print("rchen102")

decorated_func = hello_decorator(print_name)
decorated_func() 
# Hello! 
# rchen102
```
上面的步骤非常繁琐，python提供了更简单的方法(syntax sugar)
```py
def hello_decorator(print_func):
    def wrapper():
        print("Hello!")
        print_func()
    return wrapper

@hello_decorator
def print_name():
    print("rchen102")

print_name()
# Hello! 
# rchen102
```
修饰带有参数的函数
```py
def hello_decorator(print_func):
    def wrapper(*agrs, **kwargs):
        print("Hello!")
        print_func(*agrs, **kwargs)
    return wrapper

@hello_decorator
def print_name(name):
    print(name)

print_name("rchen102")
# Hello! 
# rchen102

```


参考以下两篇，对python变量进行重新梳理
[另一篇深入](https://www.jianshu.com/p/9a7eab617b22)
[python变量的实质](http://cenalulu.github.io/python/default-mutable-arguments/)
