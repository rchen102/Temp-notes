### var
推测类型，但不同于其他语言的推测类型，类型首次确认后，无法更改类型
```java
var num = 10;
num = true; // Error: incompatible types: boolean cannot be converted to int
```

### Java字符串
__目录__


__参考__
[1] [阿里云大学 | 李兴华 - Java语言基础](https://edu.aliyun.com/roadmap/java?spm=5176.13345299.1392477.3.63ddf153q7QkVf)

字符串创建
转义字符: \\, \n, \t, \", \'
+: 连接，数据转换
```java
int num1 = 1;
int num2 = 2;
String sum = "Sum = " + num1 + num2;


```