## 

参考：
[时间极客-趣谈Linux操作系统](https://time.geekbang.org/column/intro/100024701)
[waitpid函数和wait函数的用法和区别](https://blog.csdn.net/xilihong816/article/details/52900101)

### 进程创建
使用`fork()`创建一个新进程，老进程为父进程(parent process)，新进程为子进程(child process)

新建立的子进程将完全复制父进程，包括代码和环境(context)，区别在于，如果当前进程为子进程，`fork()`返回`0`，如果是父进程，返回子进程的进程号

子进程可以使用`execve`执行新的程序，`execve`之后的代码段将不会再执行

父进程可以使用wait获取子进程当前的执行情况

`pid_t wait(int *status)`
进程一旦调用`wait`，自身将被阻塞，直到`wait`找到当前进程的某个子进程已经运行完毕退出
`wait`会收集进程退出时的状态存储于`status`，若不关心状态,则可使用`wait(NULL)`
如果成功，`wait`将返回该子进程的`pid`，若调用进程无子进程，调用失败返回-1

`pid_t waitpid(pid_t pid,int *status,int options)`
本质上与`wait`相同，多出了两个参数
`pid > 0`: 只等待子进程ID等于pid的子进程
`pid = -1`: 等待任何一个子进程完成
`pid = 0`: 等待同一个进程组中的任何一个子进程

