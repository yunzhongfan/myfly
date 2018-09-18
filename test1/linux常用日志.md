## 查看日志常用命令
+ 查看带行号的日志
 显示日志行号
cat -n iuap-basedoc-defdoc.2018-09-14.log  |grep '内部码生成错误实体'

+ 查看日志前20行
head -n 20

查看linux日志

【一】从第3000行开始，显示1000行。即显示3000~3999行

cat filename | tail -n +3000 | head -n 1000

【二】显示1000行到3000行

cat filename| head -n 3000 | tail -n +1000

* 注意两种方法的顺序


    tail -n 1000：显示最后1000行

    tail -n +1000：从1000行开始显示，显示1000行以后的

    head -n 1000：显示前面1000行



## linux  文件夹操作 
回退到上个命令所在的文件夹 
cd -  或者  cd $OLDPWD。