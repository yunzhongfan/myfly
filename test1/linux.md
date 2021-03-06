# linux 



## linux 总结

https://www.linuxidc.com/Linux/2020-03/162522.htm

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

### 显示当前的目录名称 pwd 

​		pwd 显示当前的目录名称

### 文件查看 ls 命令

- ls 查看当前目录下的文件
  
- ls [选项，选项… ] 参数 … 
  
- 命令格式

   ls [选项] [目录名]  

- 常用参数：

  - -l 长格式显示文件

    • -a 显示隐藏文件

    • -r 逆序显示

    • -t 按照时间顺序显示

    • -R 递归显示
    
  - -k 即 –block-size=1K,以 k 字节的形式表示文件的大小。 

  -  -m 所有项目以逗号分隔，并填满整行行宽
     -o 类似 -l,显示文件的除组信息外的详细信息。
     -r, –reverse 依相反次序排列
     -R, –recursive 同时列出所有子目录层
     -s, –size 以块大小为单位列出所有文件的大小
     -S 根据文件大小排序 

  -  -t 以文件修改时间排序
     -u 配合 -lt:显示访问时间而且依访问时间排序
     配合 -l:显示访问时间但根据名称排序
     否则：根据访问时间排序 

- eg:

  ​     如果多个包命令的话可以 ls -lartR   或者 ls -a -l -r -t -R

    <img src="linux.assets/1587042480863.png" alt="1587042480863" style="zoom:60%;" />

<img src="linux.assets/1587472567164.png" alt="1587472567164" style="zoom: 100%;" />

### 建⽴⽬录  mkdir命令

Linux mkdir命令用于建立名称为 dirName 之子目录。

语法

```
mkdir [-p] dirName
```

**参数说明**：

 -p 确保目录名称存在，不存在的就建一个

-m <目标属性>或-mode<目标属性>建立目录的同时设置目录的权限

**目录：指定要创建的目录列表，多个目录用空格隔开**

eg:

在工作目录下，建立一个名为 AAA 的子目录 :

```
mkdir AAA
```

在工作目录下的 BBB 目录中，建立一个名为 Test 的子目录。 若 BBB 目录原本不存在，则建立一个。（注：本例若不加 -p，且原本 BBB目录不存在，则产生错误。）

```
mkdir -p BBB/Test
```

在目录/usr/meng下创建子目录 test ，并且只有文件主有读写执行权限， 其他人无权访问

> **mkdir -m 700 /usr/meng/test**

在当前目录下创建bin 和/bin/os_1 目录， 权限设置为文件主读写可执行，同组用户读写，其他用户无权访问

> **mkdir -p-m 750 bin/os_1**

### 删除目录

#### 删除空⽬录  rmdir

Linux rmdir命令删除空的目录。

语法

```
rmdir [-p] dirName
```

**参数**：

-  -p 是当子目录被删除后使它也成为空目录的话，则顺便一并删除。

eg:

- 1. 将工作目录下，名为 AAA 的子目录删除 :

- rmdir AAA

- 在工作目录下的 BBB 目录中，删除名为 Test 的子目录。若 Test 删除后，BBB 目录成为空目录，则 BBB 亦予删除

- ```
  rmdir -p BBB/Test
  ```

#### 删除⾮空⽬录   rm

Linux rm命令用于删除一个文件或者目录。

语法

```
rm [options] name...
```

**参数**：

- -i 删除前逐一询问确认。
- -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
- -r 将目录及以下之档案亦逐一删除。

实例

删除文件可以直接使用rm命令，若删除目录则必须配合选项"-r"，例如：

```
# rm  test.txt 
rm：是否删除 一般文件 "test.txt"? y  
# rm  homework  
rm: 无法删除目录"homework": 是一个目录  
# rm  -r  homework  
rm：是否删除 目录 "homework"? y
```

删除当前目录下的所有文件及目录，命令行为：

```
rm  -r  * 
```

文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。

### 复制⽂件和⽬录  cp

Linux cp命令主要用于复制文件或目录。

语法

```
cp [options] source dest
```

或

```
cp [options] source... directory
```

**参数说明**：

- -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合。
- -d：复制时保留链接。这里所说的链接相当于Windows系统中的快捷方式。
- -f：覆盖已经存在的目标文件而不给出提示。
- -i：与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖。
- -p：除复制文件的内容外，还把用户、修改时间和访问权限也复制到新文件中。
- -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
- -l：不复制文件，只是生成链接文件。

实例

使用指令"cp"将当前目录"test/"下的所有文件复制到新目录"newtest"下，输入如下命令：

```
$ cp –r test/ newtest          
```

**注意：用户使用该指令复制目录时，必须使用参数"-r"或者"-R"。**

### 移动⽂件/目录  移动、改名  mv

Linux mv 命令用来为文件或目录改名、或将文件或目录移入其它位置。

```
mv [options] source dest
mv [options] source... directory
```

**参数说明**：

- -i: 若指定目录已有同名文件，则先询问是否覆盖旧文件;
- -f: 在 mv 操作要覆盖某已有的目标文件时不给任何指示;

mv参数设置与运行结果

| 命令格式         | 运行结果                                                     |
| :--------------- | :----------------------------------------------------------- |
| mv 文件名 文件名 | 将源文件名改为目标文件名                                     |
| mv 文件名 目录名 | 将文件移动到目标目录                                         |
| mv 目录名 目录名 | 目标目录已存在，将源目录移动到目标目录；目标目录不存在则改名 |
| mv 目录名 文件名 | 出错                                                         |

实例

将文件 aaa 更名为 bbb :

```
mv aaa bbb
```

将info目录放入logs目录中。注意，如果logs目录不存在，则该命令将info改名为logs。

```
mv info/ logs 
```

再如将/usr/student下的所有文件和目录移到当前目录下，命令行为：

```
$ mv /usr/student/*  . 
```

**mv 操作文件时是移动并且重命名。**

目标目录与原目录一致，指定了新文件名，效果就是仅仅重命名。

```
mv  /home/ffxhd/a.txt   /home/ffxhd/b.txt    
```

目标目录与原目录不一致，没有指定新文件名，效果就是仅仅移动。

```
mv  /home/ffxhd/a.txt   /home/ffxhd/test/ 
或者
mv  /home/ffxhd/a.txt   /home/ffxhd/test 
```

目标目录与原目录一致, 指定了新文件名，效果就是：移动 + 重命名。

```
mv  /home/ffxhd/a.txt   /home/ffxhd/test/c.txt
```

批量移动文件和文件夹：(在Ubuntu 18.04 奏效）

例如，将 **/home/ffxhd/testThinkPHP5/tp5** 目录里边的所有文件&文件夹 挪到 **/home/ffxhd/testThinkPHP5**

```
mv  /home/ffxhd/testThinkPHP5/tp5/*  /home/ffxhd/testThinkPHP5
```

注意：需要先执行显示隐藏文件命令，否则，隐藏文件以及隐藏文件夹不会被移动到新目录。

英语点号开头的文件会被作为隐藏文件处理，英语点号开头的文件夹也被作为隐藏文件夹处理。

例如：文件 **.a.txt**， 目录 **.tp5**。

### 通配符

1 Shell常见通配符：

| **通配符**            | **含义**                                    | **实例**                                                     |
| --------------------- | ------------------------------------------- | ------------------------------------------------------------ |
| *                     | 匹配 0 或多个字符                           | a*b a与b之间可以有任意长度的任意字符, 也可以一个也没有, 如aabcb, axyzb, a012b, ab。 |
| ?                     | 匹配任意一个字符                            | a?b a与b之间必须也只能有一个字符, 可以是任意字符, 如aab, abb, acb, a0b。 |
| [list]                | 匹配 list 中的任意单一字符                  | a[xyz]b  a与b之间必须也只能有一个字符, 但只能是 x 或 y 或 z, 如: axb, ayb, azb。 |
| [!list]或[^list]      | 匹配 除list 中的任意单一字符                | a[!0-9]b a与b之间必须也只能有一个字符, 但不能是阿拉伯数字, 如axb, aab, a-b。 |
| [c1-c2]               | 匹配 c1-c2 中的任意单一字符 如：[0-9] [a-z] | a[0-9]b 0与9之间必须也只能有一个字符 如a0b, a1b... a9b。     |
| [!c1-c2]或[^c1-c2]    | 匹配不在c1-c2的任意字符                     | a[!0-9]b 如acb adb                                           |
| {string1,string2,...} | 匹配 sring1 或 string2 (或更多)其一字符串   | a{abc,xyz,123}b 列出aabcb,axyzb,a123b                        |



通配符是shell在做PathnameExpansion时用到的。说白了一般只用于文件名匹配，它是由shell解析的，比如find，ls，cp，mv等。

### 文件查找find命令

Linux find命令用来在指定目录下查找文件。任何位于参数之前的字符串都将被视为欲查找的目录名。如果使用该命令时，不设置任何参数，则find命令将在当前目录下查找子目录与文件。并且将查找到的子目录和文件全部进行显示。

语法

```
find   path   -option   [   -print ]   [ -exec   -ok   command ]   {} \;
```

**参数说明** :

find 根据下列规则判断 path 和 expression，在命令列上第一个 - ( ) , ! 之前的部份为 path，之后的是 expression。如果 path 是空字串则使用目前路径，如果 expression 是空字串则使用 -print 为预设 expression。

expression 中可使用的选项有二三十个之多，在此只介绍最常用的部份。

-mount, -xdev : 只检查和指定目录在同一个文件系统下的文件，避免列出其它文件系统中的文件

-amin n : 在过去 n 分钟内被读取过

-anewer file : 比文件 file 更晚被读取过的文件

-atime n : 在过去n天内被读取过的文件

-cmin n : 在过去 n 分钟内被修改过

-cnewer file :比文件 file 更新的文件

-ctime n : 在过去n天内被修改过的文件

-empty : 空的文件-gid n or -group name : gid 是 n 或是 group 名称是 name

-ipath p, -path p : 路径名称符合 p 的文件，ipath 会忽略大小写

-name name, -iname name : 文件名称符合 name 的文件。iname 会忽略大小写

-size n : 文件大小 是 n 单位，b 代表 512 位元组的区块，c 表示字元数，k 表示 kilo bytes，w 是二个位元组。-type c : 文件类型是 c 的文件。

d: 目录

c: 字型装置文件

b: 区块装置文件

p: 具名贮列

f: 一般文件

l: 符号连结

s: socket

-pid n : process id 是 n 的文件

你可以使用 ( ) 将运算式分隔，并使用下列运算。

exp1 -and exp2

! expr

-not expr

exp1 -or exp2

exp1, exp2

实例

将目前目录及其子目录下所有延伸档名是 c 的文件列出来。

```
# find . -name "*.c"
```

将目前目录其其下子目录中所有一般文件列出

```
# find . -type f
```

将目前目录及其子目录下所有最近 20 天内更新过的文件列出

```
# find . -ctime -20
```

查找/var/log目录中更改时间在7日以前的普通文件，并在删除之前询问它们：

```
# find /var/log -type f -mtime +7 -ok rm {} \;
```

查找前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件：

```
# find . -type f -perm 644 -exec ls -l {} \;
```

为了查找系统中所有文件长度为0的普通文件，并列出它们的完整路径：

```
# find / -type f -size 0 -exec ls -l {} \;
```

## 文本操作

### 文本的查看

 - cat: 由第一行开始显示文件内容

 - tac: 从最后一行开始显示，可以看出tac是cat的倒写形式

 - nl: 显示的时候顺便显示行号

 - more: 一页一页地显示文件内容

 -  less: 与more类似，但是比more更好的是，可以往前翻页

 -  tail: 只看结尾几行

 -  od: 以二进制的方式读取文件内容

   

   ####  tail 命令

tail 命令可用于查看文件的内容，有一个常用的参数 **-f** 常用于查阅正在改变的日志文件。

   tail  【参数】 文件...

   参数

   - ​     -f 循环读取

   - 　　-q 不显示处理信息

   - 　　-v 显示详细的处理信息

   - 　　-c<数目> 显示的字节数

   - 　　-n<行数> 显示行数

     eg: tail -n 10 test.txt  显示文件的后几行

     #### cat 命令 

      cat  [OPTION] ... [FILE]....

     参数

     **-n 或 --number**：由 1 开始对所有输出的行数编号。

     **-b 或 --number-nonblank**：和 -n 相似，只不过对于空白行不编号。

     **-s 或 --squeeze-blank**：当遇到有连续两行以上的空白行，就代换为一行的空白行。

     **-v 或 --show-nonprinting**：使用 ^ 和 M- 符号，除了 LFD 和 TAB 之外。

     **-E 或 --show-ends** : 在每行结束处显示 $。

     **-T 或 --show-tabs**: 将 TAB 字符显示为 ^I。

      **-A, --show-all**：等价于 -vET。

      **-e：**等价于"-vE"选项；

      **-t：**等价于"-vT"选项；

     也可以把多个文件的内容拼接起来多个显示

     <img src="linux.assets/1587474650502.png" alt="1587474650502" style="zoom:80%;" />

**实例**

要显示 notes.log 文件的最后 10 行，请输入以下命令：

```
tail notes.log
```

要跟踪名为 notes.log 的文件的增长情况，请输入以下命令：

```
tail -f notes.log
```

此命令显示 notes.log 文件的最后 10 行。当将某些行添加至 notes.log 文件时，tail 命令会继续显示这些行。 显示一直继续，直到您按下（Ctrl-C）组合键停止显示。

显示文件 notes.log 的内容，从第 20 行至文件末尾:

```
tail +20 notes.log
```

显示文件 notes.log 的最后 10 个字符:

```
tail -c 10 notes.log
```



#### tac 命令 

   tac [OPTION]... [FILE]...

#### nl 命令  

-b  ：指定行号指定的方式，主要有两种：
    -b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；
    -b t ：如果有空行，空的那一行不要列出行号(默认值)；
-n  ：列出行号表示的方法，主要有三种：
    -n ln ：行号在萤幕的最左方显示；
    -n rn ：行号在自己栏位的最右方显示，且不加 0 ；
    -n rz ：行号在自己栏位的最右方显示，且加 

显示的时候显示行号
![1587475320286](linux.assets/1587475320286.png)

#### more 命令

Linux more 命令类似 cat ，不过会以一页一页的形式显示，更方便使用者逐页阅读，而最基本的指令就是按空白键（space）就往下一页显示，按 b 键就会往回（back）一页显示，而且还有搜寻字串的功能（与 vi 相似），使用中的说明文件，请按 h 。

 more [-dlfpcsu] [-num] [+/ pattern] [+ linenum] [file ...]

空白键 （space） ：代表向下翻一页；
Enter ：代表向下翻“一行”；
/字串 ：代表在这个显示的内容当中，向下搜寻“字串”这个关键字；
:f ：立刻显示出文件名以及目前显示的行数；
q ：代表立刻离开 more ，不再显示该文件内容。
b 或 [ctrl]-b ：代表往回翻页，不过这动作只对文件有用，对管线无用。

- -num 一次显示的行数
- -d 提示使用者，在画面下方显示 [Press space to continue, 'q' to quit.] ，如果使用者按错键，则会显示 [Press 'h' for instructions.] 而不是 '哔' 声
- -l 取消遇见特殊字元 ^L（送纸字元）时会暂停的功能
- -f 计算行数时，以实际上的行数，而非自动换行过后的行数（有些单行字数太长的会被扩展为两行或两行以上）
- -p 不以卷动的方式显示每一页，而是先清除萤幕后再显示内容
- -c 跟 -p 相似，不同的是先显示内容再清除其他旧资料
- -s 当遇到有连续两行以上的空白行，就代换为一行的空白行
- -u 不显示下引号 （根据环境变数 TERM 指定的 terminal 而有所不同）
- +/pattern 在每个文档显示前搜寻该字串（pattern），然后从该字串之后开始显示
- +num 从第 num 行开始显示
- fileNames 欲显示内容的文档，可为复数个数

 输入了 / 之后，光标就会跑到最下面一行，并且等待你的输入， 你输入了字串并按下[enter]之后，嘿嘿！ more 就会开始向下搜寻该字串啰～而重复搜寻同一个字串，可以直接按下 n 即可啊！最后，不想要看了，就按下 q 即可离开 more 啦 

**常用操作命令**

- Enter 向下n行，需要定义。默认为1行
- Ctrl+F 向下滚动一屏
- 空格键 向下滚动一屏
- Ctrl+B 返回上一屏
- = 输出当前行的行号
- ：f 输出文件名和当前行的行号
- V 调用vi编辑器
- !命令 调用Shell，并执行命令
- q 退出more

#### less 命令

 less [参数] 文件 

 less 与 more 类似，但使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动，而且 less 在查看之前不会加载整个文件。 

**命令参数：**

-b <缓冲区大小> 设置缓冲区的大小

-e 当文件显示结束后，自动离开

-f 强迫打开特殊文件，例如外围设备代号、目录和二进制文件

-g 只标志最后搜索的关键词

-i 忽略搜索时的大小写

-m 显示类似more命令的百分比

-N 显示每行的行号

-o <文件名> 将less 输出的内容在指定文件中保存起来

-Q 不使用警告音

-s 显示连续空行为一行

-S 行过长时间将超出部分舍弃

-x <数字> 将“tab”键显示为规定的数字空格

/字符串：向下搜索“字符串”的功能

?字符串：向上搜索“字符串”的功能

n：重复前一个搜索（与 / 或 ? 有关）

N：反向重复前一个搜索（与 / 或 ? 有关）

b 向后翻一页

d 向后翻半页

u 向前滚动半页

h 显示帮助界面

Q 退出less 命令

y 向前滚动一行

空格键 滚动一行

回车键 滚动一页

[pagedown]： 向下翻动一页

[pageup]：  向上翻动一页

实例

1、查看文件

```
less log2013.log
```

2、ps查看进程信息并通过less分页显示

```
ps -ef |less
```

3、查看命令历史使用记录并通过less分页显示

```
[root@localhost test]# history | less
22  scp -r tomcat6.0.32 root@192.168.120.203:/opt/soft
23  cd ..
24  scp -r web root@192.168.120.203:/opt/
25  cd soft
26  ls
……省略……
```

4、浏览多个文件

```
less log2013.log log2014.log
```

说明：
输入 ：n后，切换到 log2014.log
输入 ：p 后，切换到log2013.log

- 附加备注

1.全屏导航

- ctrl + F - 向前移动一屏
- ctrl + B - 向后移动一屏
- ctrl + D - 向前移动半屏
- ctrl + U - 向后移动半屏

2.单行导航

- j - 向前移动一行
- k - 向后移动一行

3.其它导航

- G - 移动到最后一行
- g - 移动到第一行
- q / ZZ - 退出 less 命令

4.其它有用的命令

- v - 使用配置的编辑器编辑当前文件
- h - 显示 less 的帮助文档
- &pattern - 仅显示匹配模式的行，而不是整个文件

5.标记导航

当使用 less 查看大文件时，可以在任何一个位置作标记，可以通过命令导航到标有特定标记的文本位置：

- ma - 使用 a 标记文本的当前位置
- 'a - 导航到标记 a 处



#### 统计⽂件内容信息 wc

利用wc指令我们可以计算文件的Byte数、字数、或是列数，若不指定文件名称、或是所给予的文件名为"-"，则wc指令会从标准输入设备读取数据。

语法

```
wc [-clw][--help][--version][文件...]
```

**参数**：

- -c或--bytes或--chars 只显示Bytes数。
- -l或--lines 只显示行数。
- -w或--words 只显示字数。
- --help 在线帮助。
- --version 显示版本信息。

实例

在默认的情况下，wc将计算指定文件的行数、字数，以及字节数。使用的命令为：

```
wc testfile 
```

先查看testfile文件的内容，可以看到：

```
$ cat testfile  
Linux networks are becoming more and more common, but scurity is often an overlooked  
issue. Unfortunately, in today’s environment all networks are potential hacker targets,  
fro0m tp-secret military research networks to small home LANs.  
Linux Network Securty focuses on securing Linux in a networked environment, where the  
security of the entire network needs to be considered rather than just isolated machines.  
It uses a mix of theory and practicl techniques to teach administrators how to install and  
use security applications, as well as how the applcations work and why they are necesary. 
```

使用 wc统计，结果如下：

```
$ wc testfile           # testfile文件的统计信息  
3 92 598 testfile       # testfile文件的行数为3、单词数92、字节数598 
```

其中，3 个数字分别表示testfile文件的行数、单词数，以及该文件的字节数。

如果想同时统计多个文件的信息，例如同时统计testfile、testfile_1、testfile_2，可使用如下命令：

```
wc testfile testfile_1 testfile_2   #统计三个文件的信息 
```

输出结果如下：

```
$ wc testfile testfile_1 testfile_2  #统计三个文件的信息  
3 92 598 testfile                    #第一个文件行数为3、单词数92、字节数598  
9 18 78 testfile_1                   #第二个文件的行数为9、单词数18、字节数78  
3 6 32 testfile_2                    #第三个文件的行数为3、单词数6、字节数32  
15 116 708 总用量                    #三个文件总共的行数为15、单词数116、字节数708 
```



## 压缩与打包

最早的 Linux 备份介质是磁带，使⽤的命令是 tar

• 可以打包后的磁带⽂件进⾏压缩储存，压缩的命令是 gzip 和 bzip2

• 经常使⽤的扩展名是 .tar.gz .tar.bz2 .tg

### z j 打包命令

• 可以使⽤ gzip 和 bzip2 命令单独操作

• 通常和 tar 命令配合操作

• 常⽤参数

• -z gzip 格式压缩和解压缩

• -j bzip2 格式压缩和解压缩

### tar 打包命令

目标文件为要打包成的文件的文件名， 打包后文件的 格式取决于目标文件的后缀名

tar[必要参数][选择参数][文件] 

常⽤参数

• c 打包

• x 解包

• f 指定操作类型为⽂件



必要参数有如下：

-A 新增压缩文件到已存在的压缩

-B 设置区块大小

-c 建立新的压缩文件

-d 记录文件的差别

-r 添加文件到已经压缩的文件

-u 添加改变了和现有的文件到已经存在的压缩文件

-x 从压缩的文件中提取文件

-t 显示压缩文件的内容

**-z 支持gzip解压文件**

**-j 支持bzip2解压文件**

-Z 支持compress解压文件

-v 显示操作过程

-l 文件系统边界设置

-k 保留原有文件不覆盖

-m 保留文件不被覆盖

-W 确认压缩文件的正确性

可选参数如下：

-b 设置区块数目

-C 切换到指定目录

-f 指定压缩文件

--help 显示帮助信息

--version 显示版本信息

tar -cvf log.tar log2012.log    仅打包，不压缩！ 


tar -zcvf log.tar.gz log2012.log   打包后，以 gzip 压缩 
tar -zcvf log.tar.bz2 log2012.log  打包后，以 bzip2 压缩 

在参数 f 之后的文件档名是自己取的，我们习惯上都用 .tar 来作为辨识。 如果加 z 参数，则以 .tar.gz 或 .tgz 来代表 gzip 压缩过的 tar包； 如果加 j 参数，则以 .tar.bz2 来作为tar包名。
实例2：查阅上述 tar包内有哪些文件

命令：

tar -ztvf log.tar.gz

输出：

![img](linux.assets/20180419112811850.png)

说明：

由于我们使用 gzip 压缩的log.tar.gz，所以要查阅log.tar.gz包内的文件时，就得要加上 z 这个参数了。

实例3：将tar 包解压缩

命令：

tar -zxvf /opt/soft/test/log.tar.gz

输出：

![img](linux.assets/20180419112836566.png)


说明：

在预设的情况下，我们可以将压缩档在任何地方解开的

实例4：只将 /tar 内的 部分文件解压出来

命令：![img](linux.assets/20180419112905363.png)


输出：

![img](linux.assets/20180419112927277.png)

### gzip

## 文本编辑器 vi

多模式产⽣的原因

• 四种模式

• 正常模式 (Normal-mode) ：文件内容的粘贴、复制、删除字符或者整行删除

• 插⼊模式 (Insert-mode) 

• 命令模式 (Command-mode) 

• 可视模式 (Visual-mode) :用来对文件的块操作

### 正常模式

- 进⼊其他模式转换命令

  •   i I a A o O 进⼊插⼊模式

  i, 插入：在目前的光标所在处插入输入之文字，已存在的文字会向后退； 其中， i 为『从目前光标所在处插入』，

  I， 为『在目前所在行的第一个非空格符处开始插入』。 (常用) 

  a 为『从目前光标所在的下一个字符处开始插入』，
  
  A 为『从光标所在行的最后一个字符处开始插入』。(常用) 
  
  o 为『在目前光标所在的下一行处插入新的一行』。这是英文字母 o 的大小写；
  
  O 为在目前光标所在处的上一行插入新的一行！(常 用) 
  
  取代：r 会取代光标所在的那一个字符；R 会一直取代光标所在的文字，直到按下 ESC 为止；(常用) 
  
  •   v V ctrl+v 进⼊可视化模式
  
  •   ： 进⼊命令模式
  
  •   esc 从其他模式回到正常模式

基本操作

    	y 复制
    ​	d 剪切
    ​	p 粘贴
    ​	u 撤销
    ​	ctrl + r 重做
    ​	x 删除单个字符
    ​	r 替换单个字符
    ​	G 定位指定的⾏
    ​	^ 定位到⾏⾸
    ​	$ 定位到⾏尾
      
       一般模式： 移动光标的方法
    
    h 或 向左方向键(←) 光标向左移动一个字符 
    j 或 向下方向键(↓) 光标向下移动一个字符
    k 或 向上方向键(↑) 光标向上移动一个字符
    l 或 向右方向键(→) 光标向右移动一个字符
    如果想要进行多次移动的话，例如向下移动 30 行，可以使用 "30j" 或 "30↓" 的组合按键， 亦即加上想要进行的次数(数字)后，按下动作即可！
    [Ctrl] + [f] 屏幕『向下』移动一页，相当于 [Page Down]按键 (常用) 
    [Ctrl] + [b] 屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用) 
    [Ctrl] + [d] 屏幕『向下』移动半页
    [Ctrl] + [u] 屏幕『向上』移动半页
    + 光标移动到非空格符的下一列
    - 光标移动到非空格符的上一列
    n<space> 那个 n 表示『数字』，例如 20 。按下数字后再按空格键，光标会向右移动这一行的 n 个字符。例如 20<space> 则光标会向后面移动 20 个字符距离。  
    0或者功能键【home】  这是数字『 0 』：移动到这一行的最前面字符处 (常用)  
    $或者功能键【end】 移动到这一行的最后面字符处(常用) 
    H 光标移动到这个屏幕的最上方那一行
    M 光标移动到这个屏幕的中央那一行
    L 光标移动到这个屏幕的最下方那一行
    G 移动到这个档案的最后一行(常用) 
    nG  n 为数字。移动到这个档案的第 n 行。例如 20G 则会移动到这个档案的第 20 行(可配合 :set nu) 
    gg 移动到这个档案的第一行，相当于 1G 啊！ (常用) 
    n<Enter> n 为数字。光标向下移动 n 行(常用) 


​    
​    一般模式： 搜寻与取代
​    
    /word  向光标之下寻找一个字符串名称为 word 的字符串。例如要在档案内搜寻 vbird 这个字符串，就输入 /vbird 即可！ (常用) 
    ?word  向光标之上寻找一个字符串名称为 word 的字符串。
    n   这个n是英文按键。代表『重复前一个搜寻的动作』的意思。举例来说， 如果刚刚我们执行 /vbird 去向下搜寻 vbird 这个字符串，则按下 n 后，会向下继续搜寻下一个名称为 vbird 的字符串。如果是执行 ?vbird 的话，那么按下 n 则会向上继续搜寻名称为vbird 的字符串！
    N  这个 N 是英文按键。与 n 刚好相反，为『反向』进行前一个搜寻动作。 例如 /vbird 后，按下 N 则表示『向上』搜寻 vbird 。
    :n1,n2s/word1/word2/g  n1与n2 为数字。在第 n1 与 n2 行之间寻找 word1 这个字符串，并将该字符串取代为 word2 ！举例来说，在100到200行之间搜寻 vbird 并取代为 VBIRD 则：『:100,200s/vbird/VBIRD/g』。(常用) 
    :1,$s/word1/word2/g  从第一行到最后一行寻找 word1 字符串，并将该字符串取代为word2 ！(常用) 
    :1,$s/word1/word2/gc 从第一行到最后一行寻找 word1 字符串，并将该字符串取代为word2 ！且在取代前显示提示字符给使用者确认 (conform) 是否需要取代！(常用) 一般模式： 


​    
​    
​    删除、复制与贴上
​    
    x,X  在一行字当中，x 为向后删除一个字符 (相当于 [del] 按键)， X 为向前删除一个字符(相当于 [backspace] 亦即是退格键) (常用) 
    nx    n为数字，连续向后删除 n 个字符。举例来说，我要连续删除 10个字符， 『10x』。
    dd    删除游标所在的那一整列(常用) 
    ndd   n 为数字。删除光标所在的向下 n 列，例如 20dd 则是删除 20 列 (常用) 
    d1G   删除光标所在到第一行的所有数据
    dG    删除光标所在到最后一行的所有数据
    d$    删除游标所在处，到该行的最后一个字符
    d0    那个是数字的 0 ，删除游标所在处，到该行的最前面一个字符
    yy    复制游标所在的那一行(常用) 
    nyy   n 为数字。复制光标所在的向下 n 列，例如 20yy 则是复制 20 列 (常用) 
    y1G   复制光标所在列到第一列的所有数据
    yG    复制光标所在列到最后一列的所有数据
    y0    复制光标所在的那个字符到该行行首的所有数据
    y$    复制光标所在的那个字符到该行行尾的所有数据
    p,P  p 为将已复制的数据在光标下一行贴上，P 则为贴在游标上一行！举例来说，我目前光标在第 20 行，且已经复制了 10 行数据。则按下 p 后， 那 10 行数据会贴在原本的 20 行之后，亦即由 21 行开始贴。但如果是按下 P 呢？ 那么原本的第 20 行会被推到变成 30 行。 (常用) 
    J   将光标所在列与下一列的数据结合成同一列
    c   重复删除多个数据，例如向下删除 10 行，【 10cj 】 
    u   复原前一个动作。(常用) 
    【Ctrl】+r  重做上一个动作。(常用) 这个 u 与 【Ctrl】+r 是很常用的指令！一个是复原，另一个则是重做一次～ 利用这两个功能按键，您的编辑会更加得心应手
    .  不要怀疑！这就是小数点！意思是重复前一个动作的意思。 如果您想要重复删除、重复贴上等等动作，按下小数点『.』就好了！ (常用)    

### 命令模式

        •  :w 写⼊
        •  :q 退出
        •  :! 执⾏ Shell 命令
        •  :s 替换
        •  / 查找
        •  :set 设置命令
        :w 将编辑的数据写入硬盘档案中(常用) 
    :w! 若档案属性为『只读』时，强制写入该档案。不过，到底能不能写入， 还是跟您对该档案的档案权限有关啊！
    :q 离开 vi (常用) 
    :q! 若曾修改过档案，又不想储存，使用 ! 为强制离开不储存档案。注意一下啊，那个惊叹号 (!) 在 vi 当中，常常具有『强制』的意思～
    :wq 储存后离开，若为 :wq! 则为强制储存后离开 (常用) 
    :e! 将档案还原到最原始的状态！
    ZZ 若档案没有更动，则不储存离开，若档案已经经过更动，则储存后
    离开！
    :w  [filename] 将编辑的数据储存成另一个档案（类似另存新档）
    :r [filename] 在编辑的数据中，读入另一个档案的数据。亦即将 『filename』 这个档案内容加到游标所在行后面
    :n1,n2 w [filename] 将 n1 到 n2 的内容储存成 filename 这个档案。
    :! command 暂时离开 vi 到指令列模式下执行 command 的显示结果！例如『:! ls /home』即可在 vi 当中察看 /home 底下以 ls 输出的档案信息！
    :set nu 显示行号，设定之后，会在每一行的前缀显示该行的行号
    :set nonu 与 set nu 相反，为取消行号！


### 可视模式

        ​   v 字符可视模式
        ​	 V ⾏可视模式
        ​	 ctrl+v 块可视模式
        ​	 配合 d 和 I（⼤写 i ） 命令可以进⾏块的便利操作
        
                      区块选择的按键意义 
    v 字符选择，会将光标经过的地方反白选择！ 
    V 行选择，会将光标经过的行反白选择！ 
    [Ctrl]+v 区块选择，可以用长方形的方式选择资料 
    y 将反白的地方复制起来 
    d 将反白的地方删除掉
### 多档案编辑

将一个文本的内容一部分内容复制到另一个文本中去

多档案编辑的按键
:n 编辑下一个档案 
:N 编辑上一个档案 
:files 列出目前这个 vim 的开启的所有档案 

### 多窗口功能 

:sp [filename] 开启一个新窗口，如果有加 filename， 表示在新窗口开启一个新档案，否则表示两个窗口为同一个档案内容(同步显示)。 

[ctrl]+wj  按键的按法是：先按下 [ctrl] 不放， 再按下 w 后放开所有的按键，然后再按下 j ，则光标可移动到下方的窗口。 

[ctrl]+wk  同上，不过光标移动到上面的窗口。 

[ctrl]+wq  其实就是 :q 结束离开啦！ 举例来说，如果我想要结束下方的窗口，那么利用 [ctrl]+wj 移动到下方窗口后，按下 :q 即可离开， 也可以按下 [ctrl]+wq 啊！ 



### vim 环境设定

vim 的环境设定参数 

:set nu 还记得这个吧？！就是设定行号啊！取消的话，就是 :set nonu 

:set hlsearch  这个就是设定是否将搜寻的字符串反白的设定值。 默认值就是 hlsearch ，如果不想要反白，就 :set nohlsearch 。 

:set autoindent 是否自动缩排？autoindent 就是自动缩排， 不想要缩排就 :set noautoindent 。 

:set backup 是否自动储存备份档？一般是 nobackup 的， 如果设定 backup 的话，那么当你更动任何一个档案时，则源文件会被另存成一个档名为 filename~ 的档案。 举例来说，我们编辑 hosts ，设定 :set backup ，那么当更动 hosts 时，在同目录下，就会产生 hosts~ 文件名的档案，记录原始的 hosts 档案内容～ 

:set ruler  还记得我们提到的右下角的一些状态列说明吗？ 这个 ruler 就是在显示或不显示该设定值的啦！ 

:set showmode 这个则是，是否要显示 --INSERT-- 之类的字眼在左下角的状态列。 

:set backspace=(012) 一般来说， 如果我们按下 i 进入编辑模式后，可以利用退格键 (backspace) 来删除任意字符的。 但是，某些 distribution 则不许如此。此时，我们就可以透过 backspace 来设定啰～ 当 backspace 为 2 时，就是可以删除任意值；0 或 1 时，仅可删除刚刚输入的字符， 而无法删除原本就已经存在的文字了！ 

:set all 显示目前所有的环境参数设定值。 :syntax (off|on)   是否依据程序相关语法显示不同颜色？ 举例来说，在编辑一个纯文字文件时，如果开头是以 # 开始，那么该行就会变成蓝色。 如果您懂得写程序，那么这个 :syntax on 还会主动的帮您除错呢！但是， 如果您仅是编写纯文本文件，要避免颜色对您的屏幕产生的干扰，则可以取消这个设定 :syntax off 。 

## 文件内容查找

### grep 命令

Linux grep 命令用于查找文件里符合条件的字符串。

grep 指令用于查找内容包含指定的范本样式的文件，如果发现某文件的内容符合所指定的范本样式，预设 grep 指令会把含有范本样式的那一列显示出来。若不指定任何文件名称，或是所给予的文件名为 **-**，则 grep 指令会从标准输入设备读取数据。

语法

```
grep [-abcEFGhHilLnqrsvVwxy][-A<显示列数>][-B<显示列数>][-C<显示列数>][-d<进行动作>][-e<范本样式>][-f<范本文件>][--help][范本样式][文件或目录...]
```

**参数**：

- **-a 或 --text** : 不要忽略二进制的数据。
- **-A<显示行数> 或 --after-context=<显示行数>** : 除了显示符合范本样式的那一列之外，并显示该行之后的内容。
- **-b 或 --byte-offset** : 在显示符合样式的那一行之前，标示出该行第一个字符的编号。
- **-B<显示行数> 或 --before-context=<显示行数>** : 除了显示符合样式的那一行之外，并显示该行之前的内容。
- **-c 或 --count** : 计算符合样式的列数。
- **-C<显示行数> 或 --context=<显示行数>或-<显示行数>** : 除了显示符合样式的那一行之外，并显示该行之前后的内容。
- **-d <动作> 或 --directories=<动作>** : 当指定要查找的是目录而非文件时，必须使用这项参数，否则grep指令将回报信息并停止动作。
- **-e<范本样式> 或 --regexp=<范本样式>** : 指定字符串做为查找文件内容的样式。
- **-E 或 --extended-regexp** : 将样式为延伸的正则表达式来使用。
- **-f<规则文件> 或 --file=<规则文件>** : 指定规则文件，其内容含有一个或多个规则样式，让grep查找符合规则条件的文件内容，格式为每行一个规则样式。
- **-F 或 --fixed-regexp** : 将样式视为固定字符串的列表。
- **-G 或 --basic-regexp** : 将样式视为普通的表示法来使用。
- **-h 或 --no-filename** : 在显示符合样式的那一行之前，不标示该行所属的文件名称。
- **-H 或 --with-filename** : 在显示符合样式的那一行之前，表示该行所属的文件名称。
- **-i 或 --ignore-case** : 忽略字符大小写的差别。
- **-l 或 --file-with-matches** : 列出文件内容符合指定的样式的文件名称。
- **-L 或 --files-without-match** : 列出文件内容不符合指定的样式的文件名称。
- **-n 或 --line-number** : 在显示符合样式的那一行之前，标示出该行的列数编号。
- **-o 或 --only-matching** : 只显示匹配PATTERN 部分。
- **-q 或 --quiet或--silent** : 不显示任何信息。
- **-r 或 --recursive** : 此参数的效果和指定"-d recurse"参数相同。
- **-s 或 --no-messages** : 不显示错误信息。
- **-v 或 --revert-match** : 显示不包含匹配文本的所有行（显示出不匹配的结果）。
- **-V 或 --version** : 显示版本信息。
- **-w 或 --word-regexp** : 只显示全字符合的列。
- **-x --line-regexp** : 只显示全列符合的列。
- **-y** : 此参数的效果和指定"-i"参数相同。

1、在当前目录中，查找后缀有 file 字样的文件中包含 test 字符串的文件，并打印出该字符串的行。此时，可以使用如下命令：

```
grep test *file 
```

结果如下所示：

```
$ grep test test* #查找前缀有“test”的文件包含“test”字符串的文件  
testfile1:This a Linux testfile! #列出testfile1 文件中包含test字符的行  
testfile_2:This is a linux testfile! #列出testfile_2 文件中包含test字符的行  
testfile_2:Linux test #列出testfile_2 文件中包含test字符的行 
```

2、以递归的方式查找符合条件的文件。例如，查找指定目录/etc/acpi 及其子目录（如果存在子目录的话）下所有文件中包含字符串"update"的文件，并打印出该字符串所在行的内容，使用的命令为：

```
grep -r update /etc/acpi 
```

输出结果如下：

```
$ grep -r update /etc/acpi #以递归的方式查找“etc/acpi”  
#下包含“update”的文件  
/etc/acpi/ac.d/85-anacron.sh:# (Things like the slocate updatedb cause a lot of IO.)  
Rather than  
/etc/acpi/resume.d/85-anacron.sh:# (Things like the slocate updatedb cause a lot of  
IO.) Rather than  
/etc/acpi/events/thinkpad-cmos:action=/usr/sbin/thinkpad-keys--update 
```

3、反向查找。前面各个例子是查找并打印出符合条件的行，通过"-v"参数可以打印出不符合条件行的内容。

查找文件名中包含 test 的文件中不包含test 的行，此时，使用的命令为：

```
grep -v test *test*
```

结果如下所示：

```
$ grep-v test* #查找文件名中包含test 的文件中不包含test 的行  
testfile1:helLinux!  
testfile1:Linis a free Unix-type operating system.  
testfile1:Lin  
testfile_1:HELLO LINUX!  
testfile_1:LINUX IS A FREE UNIX-TYPE OPTERATING SYSTEM.  
testfile_1:THIS IS A LINUX TESTFILE!  
testfile_2:HELLO LINUX!  
testfile_2:Linux is a free unix-type opterating system.  
```

1. **场景：** 系统报警显示了时间，但是日志文件太大无法直接 cat 查看。(查询含有特定文本的文件，并拿到这些文本所在的行)

   解决：

   ```
   grep -n '2019-10-24 00:01:11' *.log
   ```

   查看符合条件的日志条目。

   [free-coder](javascript:;)  free-coder sun***1@126.com7个月前 (10-23)

2. 

   ### Linux 里利用 grep 和 find 命令查找文件内容

   **从文件内容查找匹配指定字符串的行：**

   ```
   $ grep "被查找的字符串" 文件名
   ```

   例子：在当前目录里第一级文件夹中寻找包含指定字符串的 .in 文件

   ```
   grep "thermcontact" /.in
   ```

   从文件内容查找与正则表达式匹配的行：

   ```
   $ grep –e "正则表达式" 文件名
   ```

   查找时不区分大小写：

   ```
   $ grep –i "被查找的字符串" 文件名
   ```

   查找匹配的行数：

   $ grep -c "被查找的字符串" 文件名

   从文件内容查找不匹配指定字符串的行：

   ```
   $ grep –v "被查找的字符串" 文件名
   ```

   从根目录开始查找所有扩展名为 .log 的文本文件，并找出包含 "ERROR" 的行：

   ```
   $ find / -type f -name "*.log" | xargs grep "ERROR"
   ```

   例子：从当前目录开始查找所有扩展名为 .in 的文本文件，并找出包含 "thermcontact" 的行：

   ```
   find . -name "*.in" | xargs grep "thermcontact"
   ```

（4）实例

　　要用好grep这个工具，其实就是要写好正则表达式，所以这里不对grep的所有功能进行实例讲解，只列几个例子，讲解一个正则表达式的写法。

$ ls -l | grep '^a'

通过管道过滤ls -l输出的内容，只显示以a开头的行。

$ grep 'test' aa bb cc

显示在aa，bb，cc文件中匹配test的行。

$ grep '\{5\}' aa

显示所有包含每个字符串至少有5个连续小写字符的字符串的行。

$ grep 'w\(es\)t.*' aa

显示所有包含west，且之后含有零个或多个任意字符的行。

（3）patten正则表达式主要参数

\ ：转义字符，忽略正则表达式中特殊字符的原有含义。
^ ：匹配以某个字符串开始的行。
$ : 匹配以某个字符串结束的行。
\<：从匹配正则表达式的行开始。
\>：到匹配正则表达式的行结束。
[ ]：在[]内个某单个字符，如[A]即A符合要求 。
[ - ] ：属于[ - ]所标记的范围字符，如[A-Z]，即A、B、C一直到Z都符合要求 。
. ：表示一定有1个任意字符。
\* ：重复前面0个或多个字符。

　　关于正则表达式的参数还有很多，这里这是列出很少的一部分，具体大家可以参照正则表达式的详解。

### egrep命令

Linux egrep命令用于在文件内查找指定的字符串。

egrep执行效果与"grep-E"相似，使用的语法及参数可参照grep指令，与grep的不同点在于解读字符串的方法。

egrep是用extended regular expression语法来解读的，而grep则用basic regular expression 语法解读，extended regular expression比basic regular expression的表达更规范。

语法

```
egrep [范本模式] [文件或目录] 
```

**参数说明：**

- [范本模式] ：查找的字符串规则。
- [文件或目录] ：查找的目标文件或目录。

实例

显示文件中符合条件的字符。例如，查找当前目录下所有文件中包含字符串"Linux"的文件，可以使用如下命令：

```
egrep Linux *
```

结果如下所示：

```
$ egrep Linux * #查找当前目录下包含字符串“Linux”的文件  
testfile:hello Linux! #以下五行为testfile 中包含Linux字符的行  
testfile:Linux is a free Unix-type operating system.  
testfile:This is a Linux testfile!  
testfile:Linux  
testfile:Linux  
testfile1:helLinux! #以下两行为testfile1中含Linux字符的行  
testfile1:This a Linux testfile!  
#以下两行为testfile_2 中包含Linux字符的行  
testfile_2:Linux is a free unix-type opterating system.  
testfile_2:Linux test  
xx00:hello Linux! #xx00包含Linux字符的行  
xx01:Linux is a free Unix-type operating system. #以下三行为xx01包含Linux字符的行  
xx01:This is a Linux testfile!  
xx01:Linux 
```

### rgrep命令

Linux rgrep命令用于递归查找文件里符合条件的字符串。

rgrep指令的功能和grep指令类似，可查找内容包含指定的范本样式的文件，如果发现某文件的内容符合所指定的范本样式，预设rgrep指令会把含有范本样式的那一列显示出来。

语法

```
rgrep [-?BcDFhHilnNrv][-R<范本样式>][-W<列长度>][-x<扩展名>][--help][--version][范本样式][文件或目录...]
```

**参说明数**：

- -? 显示范本样式与范例的说明。
- -B 忽略二进制的数据。
- -c 计算符合范本样式的列数。
- -D 排错模式，只列出指令搜寻的目录清单，而不会读取文件内容。
- -F 当遇到符号连接时，rgrep预设是忽略不予处理，加上本参数后，rgrep指令就会读取该连接所指向的原始文件的内容。
- -h 特别将符合范本样式的字符串标示出来。
- -H 只列出符合范本样式的字符串，而非显示整列的内容。
- -i 忽略字符大小写的差别。
- -l 列出文件内容符合指定的范本样式的文件名称。
- -n 在显示符合坊本样式的那一列之前，标示出该列的列数编号。
- -N 不要递归处理。
- -r 递归处理，将指定目录下的所有文件及子目录一并处理。
- -R<范本样式> 此参数的效果和指定"-r"参数类似，但只主力符合范本样式文件名称的文件。
- -v 反转查找。
- -W<列长度> 限制符合范本样式的字符串所在列，必须拥有的字符数。
- -x<扩展名> 只处理符合指定扩展名的文件名称的文件。
- --help 在线帮助。
- --version 显示版本信息。

实例

在当前目录下查找句子中包含"Hello"字符串的文件，可使用如下命令：

```
rgrep Hello * 
```

其搜索结果如下：

```
$ rgrep Hello *             #在当前目录下查找句子中包含“Hello”字符串的文件  
testfile_1:Hello 95         #testfile_1中包含“Hello”字符串的句子  
testfile_2:Hello 2005       #testfile_2中包含“Hello”字符串的句子 
```

### zgrep

zgrep 其实用法我个人觉得跟grep没什么区别。这次用zgrep 也就用上了一个 标准适用 zgrep "xxxx" path  这种。path 后面可以 指定多个目录同时grep压缩文件，速度非常快速。简直找东西福音。而且还不用把东西解压缩出来找，真是很棒。



为减少日志文件占用的空间，很多情况下我们会将日志文件以天或周为周期打包成tar.gz 包保存。虽然这样做有利空间充分利用，但当我们想查看压缩包内的内容时确很不方便。如果只是一个tar.gz文件，可以将其解压，再利用grep、awk或vi等工具查看或处理。不过如果有一个月或都一年的日志需要找出某些关键词的行，一个一个的解压，然后再看，是不是很不现实。那有没有什么简便的方法，可以不解压获得我们想要的内容呢？

答案是肯定的，可以利用zutils工具包实现。Zutils 是一组用来处理压缩文件的工具集，支持的压缩档包括：gzip, bzip2, lzip, and xz. 当前版本提供的命令有：zcat, zcmp, zdiff, and zgrep


zcat xxx.tar.gz

zcat vsftpd.tar.gz|grep --binary-files=text 'footbar.js'或
zgrep --binary-files=text 'footbar.js' vsftpd.tar.gz

### zcat

和zgrep一样，可以用于.gz 压缩过的文件，直接可以查看里面内容，和zgrep 一样如果结合管道符，必然可以找到更加丰富的用法。



### look命令

Linux look命令用于查询单词。

look指令用于英文单字的查询。您仅需给予它欲查询的字首字符串，它会显示所有开头字符串符合该条件的单字。

语法

```
look [-adf][-t<字尾字符串>][字首字符串][字典文件]
```

**参数说明**：

- -a 使用另一个字典文件web2，该文件也位于/usr/dict目录下。
- -d 只对比英文字母和数字，其余一慨忽略不予比对。
- -f 忽略字符大小写差别。
- -t<字尾字符串> 设置字尾字符串。

实例

为了查找在testfile文件中以字母L开头的所有的行，可以输入如下命令：

```
look L testfile 
```

原文件testfile中的内容如下：

```
$ cat testfile #查看testfile 文件内容  
HELLO LINUX!  
Linux is a free unix-type opterating system.  
This is a linux testfile!  
Linux test 
```

在testfile文件中使用look命令查找以"L"开头的单词，结果如下：

```
$ look L testfile                              #查找以“L”开头的单词  
Linux is a free unix-type opterating system.   #第二行以“L”开头，列出全句  
Linux test                                     #第四行以“L”开头，列出全句 
```



## ⽂件类型

• - 普通⽂件

• d ⽬录⽂件

• b 块特殊⽂件

• c 字符特殊⽂件

• l 符号链接

• f 命名管道

• s 套接字⽂件

## 进程

### Linux ps命令

Linux ps命令用于显示当前进程 (process) 的状态。

**参数：**

- -A ：所有的进程均显示出来，与 -e 具有同样的效用；
- -a ： 显示现行终端机下的所有进程，包括其他用户的进程；
- -u ：以用户为主的进程状态 ；
- x ：通常与 a 这个参数一起使用，可列出较完整信息。

**输出格式规划：**

- l ：较长、较详细的将该PID 的的信息列出；
- j ：工作的格式 (jobs format)
- -f ：做一个更为完整的输出。

ps -ef  显示出所有进程

ps -elf 显示所有的线程信息

linux查看进程所有子进程和线程

————————————————
版权声明：本文为CSDN博主「uestczshen」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/uestczshen/java/article/details/74091892





### pstree命令

Linux pstree命令将所有行程以树状图显示，树状图将会以 pid (如果有指定) 或是以 init 这个基本行程为根 (root)，如果有指定使用者 id，则树状图会只显示该使用者所拥有的行程。

使用权限：所有使用者。

语法

```
pstree [-a] [-c] [-h|-Hpid] [-l] [-n] [-p] [-u] [-G|-U] [pid|user]
```

或

```
pstree -V
```

**参数说明**：

- -a 显示该行程的完整指令及参数, 如果是被记忆体置换出去的行程则会加上括号

- -c 如果有重覆的行程名, 则分开列出（预设值是会在前面加上 *）

- ### 实例

  显示进程的关系

  ```
  pstree
  init-+-amd
  |-apmd
  |-atd
  |-httpd---10*[httpd]
  %pstree -p
  init(1)-+-amd(447)
  |-apmd(105)
  |-atd(339)
  %pstree -c
  init-+-amd
  |-apmd
  |-atd
  |-httpd-+-httpd
  | |-httpd
  | |-httpd
  | |-httpd
  ....
  ```

  特别表明在运行的进程

  ```
  # pstree -apnh //显示进程间的关系
  ```

  同时显示用户名称

  ```
  # pstree -u //显示用户名称
  ```