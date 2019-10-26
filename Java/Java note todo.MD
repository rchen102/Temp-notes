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

### 简单Java类
### 数据表与简单Java类
- 类 = 数据表
- 属性 = 基本数据列
- 引用 = 外键关联
- 实例化对象 = 数据表单行记录
- 对象数组 = 数据表多行记录


### 常量池，字符串池，包装类对象池
https://blog.csdn.net/Xu_JL1997/article/details/89150026

###
修饰符顺序 public static final int

### Object 类
- `String toString()`
  打印时被自动调用，返回值作为参数
  默认返回对象实例化的地址

- `boolean equals(Object obj)`
  使用`==`比较时，比较对象实例地址
  如果需要比较对象内容，不同的类可以根据需求覆写`equals`

### Annotation注解
JDK1.5之后新增
公共环境配置 -> 配置文件
程序配置 -> Annotation
