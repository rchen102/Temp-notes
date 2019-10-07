## Loop

参考
[codecademy Learn Python3](https://www.codecademy.com/learn/learn-python-3)

python同样支持使用`break`和`continue`关键字

- for
```python
for <temporary variable> in <list variable>:
    <action>
# or use range
for i in range(n):
  <action>
```

- while
```python
while condition:
    <action>
```

- List Comprehensions
```python
for word in words:
  if word[0] == '@':
    usernames.append(word)

# do the above actions
usernames = [word for word in words if word[0] == '@']

# can modify the value
updated_upvotes = [vote_value + 100 for vote_value in my_upvotes]
```