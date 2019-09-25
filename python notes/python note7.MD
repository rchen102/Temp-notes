## Module

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

模块的引入`from module_name import object_name`
命名空间Namespace
通常模块的命令空间与导入模块的文件分离
python默认以模块的名字作为模块的命令空间，但是可以通过别名修改
别名Alias`import module_name as name_you_pick_for_the_module`
即使是同一目录下的不同py文件，相互间作用域独立

### 常见Module

```py
# datetime
from datetime import datetime

# create a date using year, month, day as arguments
birthday = datetime(1997, 8, 30, hour, min, sec)
birthday.year # 1997
birthday.month # 8
birthday.weekday() # 返回日期对应的星期，0-6代表一到七

# create a date using datetime.now()
current_time = datetime.now()
Output: datetime.datetime(2019, 9, 24, 15, 23, 34, 411694)

datetime(2018, 1, 1) - datetime(2017, 1, 1)
Output: datetime.timedelta(days=365)

# Parsing a date using strptime
parsed_time = datetime.strptime('string', format)
datetime.strptime('Jan 15, 2018', '%b %d, %Y')
Output: datetime.datetime(2018, 1, 15, 0, 0)

# Rendering a date as a string using strftime (f: format)
date_string = datetime.strftime(datetime, format)
datetime.strftime(datetime.now(), '%b %d, %Y')
Output: 'Sep 24, 2019'

```

```py
# random
import random
random.choice() # which takes a list as an argument and returns a number from the list
random.randint() # which takes two numbers as arguments and generates a random number between the two numbers you passed in
random.sample() # takes a range and a number as its arguments. It will return the specified number of random numbers from that range

# decimal
from decimal import Decimal

```

### Virtual Environment
不同项目可能使用不同版本的python和不同版本的library
pipenv