## Linux命令

参考：
[时间极客-趣谈Linux操作系统](https://time.geekbang.org/column/intro/100024701)


### 列表
`ls`
- `-l`: 以列表(list)形式展现
- `-a`: 列出所有文件，包括隐藏文件
- `-la`: 以上两个结合
```
# ls -l
drwxr-xr-x 3 rchen102 rchen102 4096 Sep 18 20:08 coursesRegistration
-rw-r--r-- 1 rchen102 rchen102 2494 Sep 18 21:29 README.md
```
第一个字段：第一个字符是__文件类型__，`d`表示目录，`-`表示普通文件，接着9位为__权限位__，3个一组，每一组`rwx`表示读(read)，写(write)，执行(execute)，3组分别代表文件所属用户权限、文件所属的组(group)权限和其他用户权限

第二个字段：硬链接(hard link)数组

第三、四个字段：所属用户，所属组

第五个字段：文件大小

### 软件安装
Linux两大体系，CentOS和Ubuntu，分别使用rpm和deb软件安装包，以下主要以Ubuntu为主

- 安装命令：
`dpkg -i jdk-XXX_linux-x64_bin.deb`
- 查看已安装软件
`dpkg -l`
- 删除软件
`dpkg -r`

也可以使用`apt-get`管理软件的下载安装卸载
`apt-get install`
`apt-get purge`




