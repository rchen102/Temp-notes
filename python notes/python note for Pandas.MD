## Pandas

参考
[Dataquest | Introduction to Pandas](https://app.dataquest.io/m/291/introduction-to-pandas)

```py
# 属性
df.shape
df.dtype
df.info() # automatically print info

# 访问前6行或后8行
f500_head = f500.head(6)
f500_tail = f500.tail(8)

# 访问指定位置
df.loc[row_label, column_label]

# shortcut
df[column_label]
df.loc[row_label]
```

Series (1 dimension)
```py
Series.value_counts() # count each unique value
Series.loc[]
Series.describe()
```