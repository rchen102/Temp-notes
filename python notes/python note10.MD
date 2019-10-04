## Class

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

### 定义
使用关键字`class`定义类
类的命名遵从Pascal Case(每个单词首字母大写，不使用下划线)
class is a schematic for a data type and an object is an instance of a class

```py
class ClassName:
    pass

# instantiate
class_instance = ClassName()
print(type(class_instance))
# "<class '__main__.ClassName'>"
# __main__: the current file we're running
```


### 方法
方法(Method)的第一个参数self为调用该方法的对象本身(refers to the object calling the function)
实例(instance)调用方法时，会隐式的传递实例自己作为参数之一，因此方法的声明都需要`self`参数


```py
class Dog:
  dog_time_dilation = 7

  def time_explanation(self):
    print("Dogs experience {} years for every 1 human year.".format(self.dog_time_dilation))
```

### 构造器
构造器(Construtor)也称(init method)为class中的特殊方法之一(dunder)
(double-underscore abbreviated to “dunder”)

`__init__`： 构造器，在实例创建时，负责初始化
```py
def __init__(self):
    print("Hello")
```

### 属性
属性(Attribute)包含了class variables和instance variables
方法(Method)也可以认为是一种attribute(函数也是对象)
```py
class Musician: 
    title = "Rockstar"  #class variable
m1 = Musician()
m1.age = 15 #instance variable

# 使用arguments创建instance variable
class SearchEngineEntry:
    def __init__(self, url):
        self.url = url
wikipedia = SearchEngineEntry("www.wikipedia.org")
print(wikipedia.url) # prints "www.wikipedia.org"

```

如果试图访问不存在的attribute则会引起`AttributeError`
若不确定attribute是否存在: `hasattr()`和`getattr()`(也可判断方法)
```py
# AttributeError
class NoCustomAttributes:
    pass

attributeless = NoCustomAttributes()

try:
    attributeless.fake_attribute
except AttributeError:
    print("This text gets printed!") # prints "This text gets printed!

# 判断attribute是否存在
hasattr(attributeless, "fake_attribute") # returns False
getattr(attributeless, "other_fake_attribute", 800) # returns 800, the default value
```

Everything is Object (Even function)
都可以使用`dir(instance)`来获取全部的属性
python会自动添加一部分属性(internal attributes),通常由`__name__`标识
```py
class FakeDict:
  pass

fake_dict = FakeDict()
fake_dict.attribute = "Cool"

dir(fake_dict)
# Prints ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'attribute']

```

### String representation
如果直接print对象，会得到对象定义的位置和存储的地址
可以使用`__repr__`方法自定义打印值，返回值必须为String
```py
class Employee():
  def __init__(self, name):
    self.name = name

argus = Employee("Argus Filch")
print(argus)
# prints "<__main__.Employee object at 0x104e88390>"


class Employee():
  def __init__(self, name):
    self.name = name

  def __repr__(self):
    return self.name

argus = Employee("Argus Filch")
print(argus)
# prints "Argus Filch"
```

### 继承
python支持继承(Inheritance)，被继承的类为父类(parent/base)，使用继承的类为子类(child)
`issubclass(child, base)`: 判断child是否继承了base class

__继承语法__
```py
class User:
    is_admin = False
    def __init__(self, username)
    self.username = username

class Admin(User):
    is_admin = True
```


__方法重写__
```py
class User:
    def __init__(self, username, permissions):
        self.username = username
        self.permissions = permissions

    def has_permission_for(self, key):
        if self.permissions.get(key):
            return True
        else:
            return False

class Admin(User):
    def has_permission_for(self, key):
        return True  
```

__super()__
可以使用super()访问父类(super class)的方法，属性

```py
class Sink:
    def __init__(self, basin, nozzle):
        self.basin = basin
        self.nozzle = nozzle

class KitchenSink(Sink):
    def __init__(self, basin, nozzle, trash_compactor=None):
        super().__init__(basin, nozzle)
        if trash_compactor:
            self.trash_compactor = trash_compactor
```

### 接口
python中同样有接口(Interface)的概念
当不同的class拥有相同的属性和方法名称时，就认为他们实现了相同的接口

```py
class Chess:
    def __init__(self):
        self.board = setup_board()
        self.pieces = add_chess_pieces()

    def play(self):
        print("Playing chess!")

class Checkers:
    def __init__(self):
        self.board = setup_board()
        self.pieces = add_checkers_pieces()

    def play(self):
        print("Playing checkers!")

chess_game = Chess()
checkers_game = Checkers()
play_game(chess_game) # prints "Playing chess!"
play_game(checkers_game) # prints "Playing checkers!"
```

### Dunder Methods
offer a way to override builtin method
```py
class Color: 
  def __add__(self, other): # override + 
    """
    Adds two RGB colors together
    Maximum value is 255
    """
    new_red = min(self.red + other.red, 255)
    new_blue = min(self.blue + other.blue, 255)
    new_green = min(self.green + other.green, 255)

    return Color(new_red, new_blue, new_green)

red = Color(255, 0, 0)
blue = Color(0, 255, 0)
green = Color(0, 0, 255)

magenta = red + blue # Color with RGB: (255, 255, 0)
cyan = blue + green # Color with RGB: (0, 255, 255)
```

Make a class like List
```py
class UserGroup:
    def __init__(self, users, permissions):
        self.user_list = users
        self.permissions = permissions

    def __iter__(self):
        return iter(self.user_list)

    def __len__(self):
        return len(self.user_list)

    def __contains__(self, user):
        return user in self.user_list

class User:
    def __init__(self, username):
        self.username = username

# Use them
diana = User('diana')
frank = User('frank')
jenn = User('jenn')

can_edit = UserGroup([diana, frank], {'can_edit_page': True})
can_delete = UserGroup([diana, jenn], {'can_delete_posts': True})

print(len(can_edit))
# Prints 2

for user in can_edit:
    print(user.username) # Prints "diana" and "frank"

if frank in can_delete:
    print("Since when do we allow Frank to delete things? Does no one remember when he accidentally deleted the site?")
```

