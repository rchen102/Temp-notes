### var
推测类型，但不同于其他语言的推测类型，类型首次确认后，无法更改类型
```java
var num = 10;
num = true; // Error: incompatible types: boolean cannot be converted to int
```

### Java字符串
__目录__

字符串创建
转义字符: \\, \n, \t, \", \'
+: 连接，数据转换
```java
int num1 = 1;
int num2 = 2;
String sum = "Sum = " + num1 + num2;
```

### 数组
默认值是对应类型的默认值
数组排序: Arrays.sort()
数组拷贝: System.arraycopy()

### 可变参数
JDK 1.5之后支持的新特性
本质: 自动封装为数组
调用时，即可以直接传入数组，也可以传入可变长度参数
```java
public int sum(int ... num) {
    int sum = 0;
    for (int n : num) {
        sum += n;
    }
    return sum;
}

sum(1,2,3);
sum({1,2,3});



```
