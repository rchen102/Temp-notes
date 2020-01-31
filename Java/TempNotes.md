## 字符串对象池
- 本质是一个`HashTable`，池中存储的是字符串对象的引用
- 创建字符串常量时，如果对象池中该字符串已经存在，将直接引用对象池中的字符串对象
- 避免内存空间频繁的开辟和释放影响系统性能


### 字符串对象创建
__直接赋值__ `String str = "Hello";` 
1. 查找常量池中是否含有`"Hello"`对象  
    + 有,返回对应字符串实例的引用
    + 没有，创建一个实例对象并入池
  
__构造方法__ `String str = new String("Hello");`  
1. 查找常量池中是否含有`"Hello"`对象
    + 有,返回对应字符串实例的引用(此处返回并不是`new String()`的返回)
    + 没有，创建一个实例对象(注意，此处并不会入池，可以使用`intern()`手动入池)

2. 在堆中创建(new)一个Stirng对象(以`“Hello"`调用new方法)
3. 将对象的引用赋值给`str`

::: warning 注意
如果常量池中没有`Hello`对象，则`new String("Hello")`开辟了**两次**内存(产生了垃圾空间)，否则只是开辟一次内存
::: 


```java
String str1 = "Hello";  // "Hello"自动入池
String str2 = "Hello";  // 直接获得已存在的"Hello"的引用(地址相同)
String str3 = new String("Hello"); // 到目前为止，开辟了2块空间

str1 == str2; // True
str1 == str3; // False
```