## 控制流 (control flow)

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

### 条件语句 conditional statements

python不支持三目运算符，但是可以利用`if`, `else`实现

```python
def checkNumber(num):
    if num > 0:
        return "Positive"
    elif num < 0:
        return "Negative"
    else:
        return "Zero"

# Implement ternary operator
return x if x > y else y
```

### Error Except
使用关键字`try`, `Except`
```python
try:
    # some statement
except ErrorName:
    # some statement
```

raise和throw区别
```py
class KitchenException(Exception):
    """
    Exception that gets thrown when a kitchen appliance isn't working
    """
class MicrowaveException(KitchenException):
    """
    Exception for when the microwave stops working
    """
class RefrigeratorException(KitchenException):
    """
    Exception for when the refrigerator stops working
    """
def get_food_from_fridge():
  if refrigerator.cooling == False:
    raise RefrigeratorException
  else:
    return food

def heat_food(food):
  if microwave.working == False:
    raise MicrowaveException
  else:
    microwave.cook(food)
    return food

try:
  food = get_food_from_fridge()
  food = heat_food(food)
except KitchenException:
  food = order_takeout()
```