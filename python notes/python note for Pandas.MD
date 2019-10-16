## Pandas

参考
[Dataquest | Introduction to Pandas](https://app.dataquest.io/m/291/introduction-to-pandas)


__创建__
```py
import pandas as pd
df = pd.DataFrame()
sr = pd.Series()
```

__访问__
```py
# 访问前6行或后8行
f500_head = f500.head(6)
f500_tail = f500.tail(8)

# loc: label based selection
df.loc[row_label, column_label]
df[column_label] # shortcut
df.loc[row_label] # shortcut

# iloc: integer position based selection
df.iloc[row, column]
df[column]
df.loc[row]
```

__操作__
```py
# 属性
df.shape
df.dtype
df.info() # automatically print info

df.describe() # give general statistical description
df.values_counts() # unique values counts 
df.sort_values() # sort by values
```

### Series
```py
Series.value_counts() # count each unique value
Series.loc[]
Series.describe()
Series.isnull()
Series.notnull()
```