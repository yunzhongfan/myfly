## git add -A 和 git add . 的区别 

git add -A和 git add .   git add -u在功能上看似很相近，但还是存在一点差别

**git add** . ：他会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

**git add -u** ：他仅监控已经被add的文件（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

**git add -A** ：是上面两个功能的合集（git add --all的缩写）

- 总结

·  git add -A  **提交所有变化**

·  git add -u  **提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)**

·  git add .  **提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件**

********


##Git中git commit -m 与git commit -a -m  的区别 
一般仓库中的文件可能存在于这三种状态：

1）**Untracked files** → 文件未被跟踪；

2）**Changes to be committed** → 文件已缓存，这是下次提交的内容；

3）**Changes bu not updated** → 文件被修改，但并没有添加到缓存区。

**git commit -m **  只会提交添加到缓存区的文件**（**只提交添加的**）

**git commit -a -m ** 能提交修改过，但是没有添加到缓存区的文件（**修改过的就能提交**）

**git commit -a**   就是自动去把之前标记过的文件再标记上，包括删除的文件，但是不包括新增的文件。

使用命令：git log  能查看提交历史，后面加上  --pretty=oneline  能使内容单行显示

使用命令：git status  能让我们时刻掌握仓库当前的状态






