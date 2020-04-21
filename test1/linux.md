# linux 



## 万能的帮助命令

### man 帮助

- ​	man 是 manual 的缩写，

- man 帮助用法演示：
  - # man ls

- man 也是一条命令，分为 9 章，可以使用man 命令获得 man 的帮助
  - man 也是⼀条命令，分为 9 章，可以使⽤ man 命令获得 man 的帮助

### help 帮助

- shell（命令解释器）⾃带的命令称为内部命令，其他的是外部命令
- 内部命令使用 help 帮助
  - \# help cd
- 外部命令使⽤help帮助
  - \# ls --help

### info 帮助

- info 帮助比 help 更详细，作为 help 的补充
  - \# info ls

## 文件操作

### 显示当前的目录名称

​		pwd 显示当前的目录名称

### 文件查看

- ls 查看当前目录下的文件
  - ls [选项，选项… ] 参数 … 

- 常用参数：

  - -l 长格式显示文件

    • -a 显示隐藏文件

    • -r 逆序显示

    • -t 按照时间顺序显示

    • -R 递归显示

- eg:

  ​     如果多个包命令的话可以 ls -lartR   或者 ls -a -l -r -t -R

    <img src="linux.assets/1587042480863.png" alt="1587042480863" style="zoom:60%;" />





